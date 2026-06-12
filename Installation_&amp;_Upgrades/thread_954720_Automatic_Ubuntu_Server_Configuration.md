---
title: "Automatic Ubuntu Server Configuration"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by mmond on 2008-10-21
Hiya,

I created a bash script that remotely connects to a bare Hardy server install and configures it as a working Rails web application server.  

Check out the blog entry at FiveRuns for details:  
[http://blog.fiveruns.com/2008/10/20/automatic-production-rails](http://blog.fiveruns.com/2008/10/20/automatic-production-rails)

In summary:
The script connects to a new Ubuntu 8.04 server and configures all necessary applications and libraries.  You only need to provide 2 pieces of information: the target address of your server and the password. 

The script installs the following, sets up the database and turns on the services: 
[LIST]
[*]Ruby 1.8.6 
[*]Rubygems 1.2 
[*]Sqlite3 
[*]MySQL 5.0.51a 
[*]Thin 0.8.2 
[*]nginx 0.5.33
[*]Mongrel 1.1.5
[*]Eldorado Rails application
[*]Capistrano deployment
[*]Rubygems 1.3
[/LIST]

Feel free to check out everything at Github.  Enjoy!
[http://github.com/mmond/configuration-automation/tree](http://github.com/mmond/configuration-automation/tree)

Mark

---

