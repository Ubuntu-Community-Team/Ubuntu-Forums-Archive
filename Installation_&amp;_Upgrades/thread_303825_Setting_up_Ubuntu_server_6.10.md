---
title: "Setting up Ubuntu server 6.10"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by Bill007 on 2006-11-20
I have just installed the ubuntu 6.10

lamp version

do i need to set up webmin  etc 

and can some one point me to a good  tutorial for setting up this production server

Kind Regards Bill Bailey

---

### Post by mssever on 2006-11-20
What are you trying to accomplish? What is your skill level? I don't use webmin, but many people do. Personally, I prefer to edit config files directly.

What kind of setup tutorial do you want? You can try Googling ```
"perfect setup" ubuntu lamp
``` for one person's idea, but it may or may not meet your needs.

---

### Post by Bill007 on 2006-11-20
Skill level is growing fast but still a learner

Im working off the command line ok but have to ask a lot  of questions in the forum 

Just spent 7 days trying to configure 5.10  
downloaded Apache2 perl PHP5 MYSQL UNZIPED AND MOVE TO CORRECT DIRECTORIES

only to find that the 5.10 kernel didnt have the drivers for a realtek network card so have just downloaded 6.10 and yes I can see the network cards eth0 eth1 

Thought WEBMIN or some other interface might help ease the learning curve 

Reason for server

Wanting to set up a production server for my my web designing I like to use PHP5  and MYSQL mainly

Thought also that i would like to save some files from my Business in acentral place I have a small network and feel exposed to data loss on my individual machines 

Can I set it up as a DNS server too 

I have a once a week Game night(Ghost recon) between two other freinds and thought i might like to host it at some point

am I best to do this when first installing I noted the option of lamp or DNS 

am I better to set it up as DNS and down load the packages i need

Thank you for your Time

---

### Post by mssever on 2006-11-21
One of the best things about Debian and friends (including Ubuntu) is the way you install programs. Unless you have a specific reason to do so, you shouldn't download programs directly, like Windows. Instead, if you use a graphical environment, use Synaptic to search for and add/remove programs. From the command line, use aptitude and friends. Here's a ruby script I found somewhere that greatly simplifies command line package management ```
#!/usr/bin/env ruby                
# -*- mode: ruby; backup-inhibited:t -*-
#
# Utility to ease my life with apt
#

def help_text
  print <<-EOP
  Usage:
    rapt file    <file name> - (-f)   find package owner of file (slow!)
    rapt show    <pkg-name>  - (-sh)  equivalent to "apt-cache show"
    rapt showpkg <pkg-name>  - (-sp)  equivalent to "apt-cache showpkg"
    rapt search  <pkg-name>  - (-s)   equivalent to "apt-cache search"
    rapt source  <pkg-name>  - (-src) equivalent to "apt-get source"
    rapt install <pkg-name>  - (-i)   equivalent to "apt-get install"
    rapt install <pkg-name>  - (-I)   equiv. to "apt-get -t unstable install"
    rapt list    <pkg-name>  - (-l)   equivalent to "dpkg --list"
    rapt purge   <pkg-name>  - (-p)   equivalent to "dpkg --purge"
    rapt update              - (-u)   apt update
    rapt refresh             - (-U)   apt update /upgrade
    rapt remove  [pkg-name]  - (-r)   apt-get remove
    rapt dist-upgrade [pkgs] - (-d)   apt-get dist-upgrade

  Combine commonly used commands in Debian apt/dpkg system into a
  unified command line interface.

  EOP
end


def smart_exec( estr )
  puts "Exec string: #{estr}" if $DEBUG
  exec( estr )
end


# could do this with a hash table, might be a tad cleaner
# if we add more functions  
case ARGV.shift
when 'autoclean'
  smart_exec("apt-get autoclean")  

when 'clean'
  smart_exec("apt-get clean")

when 'file', '-f'
  smart_exec("dpkg --search #{ARGV.join(' ')}")

when 'show', '-sh'
  smart_exec("apt-cache show #{ARGV.join(' ')}")

when 'showpkg', '-sp'
  smart_exec("apt-cache showpkg #{ARGV.join(' ')}")

when 'search', '-s'
  smart_exec("apt-cache search #{ARGV.join(' ')}")

when 'source', '-src'
  smart_exec("apt-get source  #{ARGV.join(' ')}")

when 'install', '-i'
  smart_exec("apt-get install #{ARGV.join(' ')}")

when 'uinstall', '-I'
  smart_exec("apt-get -t unstable install #{ARGV.join(' ')}")

when 'list', '-l'
  smart_exec("dpkg --list #{ARGV.join(' ')}")

when 'purge', '-p'
  smart_exec("dpkg --purge #{ARGV.join(' ')}")

when 'remove', '-r'
  smart_exec("apt-get remove #{ARGV.join(' ')}")

when 'upgrade'    
  smart_exec("apt-get upgrade --show-upgraded #{ARGV.join(' ')}")

when 'dist-upgrade', '-d'    
  smart_exec("apt-get dist-upgrade #{ARGV.join(' ')}")
    
when 'refresh', '-U'
  smart_exec("apt-get update; apt-get upgrade --show-upgraded")

when 'update', '-u'
  smart_exec("apt-get update")

else
  help_text
  
  if $DEBUG
    puts
    puts "Unrecognized argument '#{ARGV[0]}'"
  end
  exit(0)
end
``` Save it as /usr/local/bin/rapt and make it executable (sudo chmod +x /usr/local/bin/rapt). Type rapt for usage instructions.

All this to say that to get what you want setup, just do ```
sudo rapt install php5-mysql mysql phpmyadmin bind9
``` (bind9 is the DNS server; phpmyadmin is a web-based admin app for mysql) Search (using rapt search) for anything else you might want. rapt showpkg package-name gives more detailed info.

It certainly wouldn't hurt to try webmin--especially if you install it from the repositories.

For a fileserver, you have basically two options: Samba uses the protocols that Windows computers understand (and Linux and Mac computers can be configured to use it, as well), and NFS is ideal for native Linux/UNIX use.

Some links:[LIST]
[*][DNS Howto]("http://tldp.org/HOWTO/DNS-HOWTO.html")
[*][Installing software]("http://psychocats.net/ubuntu/installingsoftware") (You'll save yourself a lot of headaches in the future if you install from the repositories whenever possible.)[URL="http://psychocats.net/ubuntu/installingsoftware"]
[/URL]
[*][Enabling additional repositories]("http://psychocats.net/ubuntu/sources")[/LIST]

---

### Post by Bill007 on 2006-11-21
OH thank you so much what a great push in the right direction most appreciative

there is enough info there to keep me shut up for awhile 

thanks for the ruby script 

Kind regards Bill007:D

---

