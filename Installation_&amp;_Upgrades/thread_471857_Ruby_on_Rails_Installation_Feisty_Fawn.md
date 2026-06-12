---
title: "Ruby on Rails Installation Feisty Fawn"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by isaac_sloan on 2007-06-12
Over the past year I've found that this is everything required for most RoR applications. 
Type : sudo echo "Installing Ruby on Rails"
Then just paste the following into your console and it will install ruby, irb, ri, rubygems, mysql and everything required for that to work with ruby, rmagick and its dependencies, Rails and the postgres database adapter in case you plan on using that... Hope this helps.

```

echo "installing everything ruby.."
sudo apt-get install ruby ri rdoc mysql-server libmysql-ruby ruby1.8-dev irb1.8 libdbd-mysql-perl libdbi-perl libmysql-ruby1.8 libmysqlclient15off libnet-daemon-perl libplrpc-perl libreadline-ruby1.8 libruby1.8 mysql-client-5.0 mysql-common mysql-server-5.0 rdoc1.8 ri1.8 ruby1.8 rubygems build-essential 

sudo gem install rails --include-dependencies
echo "install postgres adapter."
sudo gem installing postgres-pr

echo "installing dependencies for rmagick."
sudo apt-get remove --purge librmagick-ruby-doc librmagick-ruby1.8
sudo apt-get install libmagick9-dev ruby1.8-dev

echo "installing rmagick"
wget http://rubyforge.org/frs/download.php/19089/rmagick-1.15.5.gem
sudo gem install rmagick-1.15.5.gem
```

echo "Installation Complete."

---

