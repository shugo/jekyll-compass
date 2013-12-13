require 'cane/rake_task'

desc "Run code sanity checks"
Cane::RakeTask.new(:sanity) do |cane|
  cane.canefile = '.cane'
end

desc "Build the gem"
task :build => :sanity do
  sh 'gem', 'build', *Dir['*.gemspec']
end

desc "Cleans unneeded or old files"
task :clean do
  files = Dir['*.gem']
  rm_rf *Dir['*.gem'] unless files.empty?
end

desc "Install locally"
task :install => [:clean, :build] do
  sh 'gem', 'install', *Dir['*.gem']
end
