---
title: "Redmine and Sendmail - Can't send mail from server"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by SiLeNCeD_x on 2011-01-22
Hello All,

I couldn't find a relevant post for this, so I thought I'd start here. I've toyed around off and on for years on Ubuntu, so my knowledge tends to be spotty. Let me apologize in advance for that now lol.

I'm currently running Ubuntu 10.10 Server using VirtualBox 3.2.12 r68302. I've setup a LAMP Server and Installed Redmine and I'm going to be starting some projects. The problem I have is that I've linked it to a subdomain thru my hosting, so things are a little more complex for me then usual. Here's the software I've added for this setup:

Ruby version              1.8.7 (i686-linux)
RubyGems version          1.3.7
Rack version              1.1
Rails version             2.3.5
Active Record version     2.3.5
Active Resource version   2.3.5
Action Mailer version     2.3.5
Active Support version    2.3.5
Edge Rails revision       unknown
Application root          /usr/share/redmine
Environment               production
Database adapter          mysql
Database schema version   20100705164950

Sendmail version: 8.14.3-9.2

What I'm attempting to do is as follows:

* I own 'example.com' (hosting is remote/not my server) and want 'ip.example.com' to be the specific target for my virtual Ubuntu Server.
* MX Records have been updated at my hosting provider to point ip.example.com to my ISP's IP Address. We'll use 20.20.20.20 for the example (in case it needs to be added in my hosts file later on) of my external IP address and my actual server is locally running on 192.168.1.111
* I've setup Redmine and can connect to it via [http://ip.example.com/redmine](http://ip.example.com/redmine)
* I've setup my /etc/hosts file as follows
127.0.0.1     localhost
127.0.1.1     ip
192.168.1.111 ip.example.com ip
* I'm having issues getting e-mails off my server and out of Redmine using Sendmail. CLI-wise, I'm using MUTT as a local e-mail program and can send e-mails between users, but nothing can leave the server.
* In Redmine, my /etc/redmine/default/email.yml file looks like this:
production:
   delivery_method: :sendmail
   smtp_settings:
     address: smtp.remotehost.com
     port: 587 #I've also used the standard 25
     domain: example.com
     authentication: :login
     user_name: [email]me@example.com[/email]
     password: 'password'

I think all-in-all, I'm pretty much confusing myself lol. This is probably more of a sendmail issue then anything and I was wondering if maybe someone could give me some advise on how to proceed. My main confusion is about how mail server functionality works as well as how to properly set the host of the virtual pc.

Any thoughts? Thanks in advance

---

### Post by SiLeNCeD_x on 2011-01-22
Am I not asking the right questions? Maybe I should start smaller. My /etc/hosts file... does it seem wrong for what I'm attempting to do? I know if this isn't setup correctly, it can cause many other issues configuration-wise:

127.0.0.1 localhost
127.0.1.1 ip
192.168.1.111 ip.example.com ip

I tried an alternative approach with:

127.0.0.1 localhost
127.0.1.1 ip.example.com
192.168.1.111 ip.example.com ip

and

127.0.0.1 ip.example.com
127.0.1.1 ip.example.com
192.168.1.111 ip.example.com ip

and that just gives me errors. Mostly:
Error sending message, child exited 67 (User unknown.)

Please help. I'm almost done and just about ready to backup this server in case I break something else later down the road :)

---

