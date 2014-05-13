require 'rubygems'
require 'bundler'
require 'rspec'

$:.unshift(File.dirname(__FILE__) + '/lib')
require 'net/dns'


# Run test by default.
task :default => [:spec]

require 'rake'
require 'rspec/core/rake_task'

RSpec::Core::RakeTask.new(:spec) do |t|
  t.pattern = FileList['spec/**/*_spec.rb']
  t.rspec_opts = ["-r ./spec/spec_helper.rb"]
end

require 'yard'

YARD::Rake::YardocTask.new(:yardoc) do |y|
  y.options = ["--output-dir", "yardoc"]
end

namespace :yardoc do
  task :clobber do
    rm_r "yardoc" rescue nil
  end
end

task :clobber => "yardoc:clobber"


desc "Open an irb session preloaded with this library"
task :console do
  sh "irb -rubygems -I lib -r net/dns.rb"
end
