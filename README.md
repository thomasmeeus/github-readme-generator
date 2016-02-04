Github README Generator
=======================

`github-readme-generator` lets you generate a `README.md` file simply.

# Example

```ruby
# Rakefile
require 'github_readme_generator/task'

GitHubReadmeGenerator::RakeTask.new :readme do |config|
  config.title = 'FreeRADIUS Puppet module'  # Dynamic using github lib?
  config.badges = {
    :puppetforge_version => {
      :badge   => :puppetforge,
      :type    => 'v',
      :user    => 'raphink',    # Dynamic from metadata.json?
      :project => 'freeradius', # Dynamic from metadata.json?
    },
    :puppetforge_downloads => {
      :badge   => :puppetforge,
      :type    => 'dt',
      :user    => 'raphink',    # Dynamic from metadata.json?
      :project => 'freeradius', # Dynamic from metadata.json?
    },
    :travis => {
      :badge   => :travis,
      :user    => 'raphink', # Dynamic from git
      :project => 'puppet-freeradius', # Dynamic from git?
    },
    :jenkins => {
      :badge        => :jenkins,
      :jenkins_url  => 'https://myjenkinsinstance.com/job/puppet-freeradius'
    },
  }
end
```
It's also possible to generate documentation for a puppet-module that's not resides in the same directory as your Rakefile. This can be done by setting a `MODULE_PATH` environment variable.

## Dependencies

It's required to install the 'Embeddable Build Status'-plugin in Jenkins if you want to embed Jenkins' build badges.
