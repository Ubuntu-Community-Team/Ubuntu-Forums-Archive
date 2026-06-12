---
title: "Metasploit Install"
date: 2017-06-01
forum: Installation &amp; Upgrades
---

### Post by chaz72 on 2017-06-01
Hello. I wanted to install Metasploit on my Ubuntu 14.04 laptop. I went through the below guide step by step and when I go to run msfconsole I get the below. Can anyone be of assistance? 

<snip> - Install Guide

Error:

cscecela@Kalibu:/opt/metasploit-framework$ msfconsole
/home/cscecela/.rvm/rubies/ruby-2.4.1/lib/ruby/2.4.0/psych.rb:377:in `parse': (/opt/metasploit-framework/config/database.yml): could not find expected ':' while scanning a simple key at line 5 column 2 (Psych::SyntaxError)
    from /home/cscecela/.rvm/rubies/ruby-2.4.1/lib/ruby/2.4.0/psych.rb:377:in `parse_stream'
    from /home/cscecela/.rvm/rubies/ruby-2.4.1/lib/ruby/2.4.0/psych.rb:325:in `parse'
    from /home/cscecela/.rvm/rubies/ruby-2.4.1/lib/ruby/2.4.0/psych.rb:252:in `load'
    from /home/cscecela/.rvm/rubies/ruby-2.4.1/lib/ruby/2.4.0/psych.rb:473:in `block in load_file'
    from /home/cscecela/.rvm/rubies/ruby-2.4.1/lib/ruby/2.4.0/psych.rb:472:in `open'
    from /home/cscecela/.rvm/rubies/ruby-2.4.1/lib/ruby/2.4.0/psych.rb:472:in `load_file'
    from /opt/metasploit-framework/lib/msf/ui/console/driver.rb:179:in `initialize'
    from /opt/metasploit-framework/lib/metasploit/framework/command/console.rb:62:in `new'
    from /opt/metasploit-framework/lib/metasploit/framework/command/console.rb:62:in `driver'
    from /opt/metasploit-framework/lib/metasploit/framework/command/console.rb:48:in `start'
    from /opt/metasploit-framework/lib/metasploit/framework/command/base.rb:82:in `start'
    from /usr/local/bin/msfconsole:48:in `<main>'

Thanks,

Chaz.

---

### Post by QIII on 2017-06-01
Please read the [Ubuntu Forums Rules]("https://ubuntuforums.org/misc.php?do=showrules"), especially:

> Cracking: Requests for help about any form of password or encryption "cracking" are not supported. Even though there are packages such as aircrack in the repositories, discussions about cracking or software related to cracking often lead to discussions about illegal activities. Such threads will be closed.

We consider pen testing to be in this category.  Although we have no reason to doubt that your intentions are anything but the best, answering such requests for support would be of benefit also to those with nefarious intent.  We do not want the Ubuntu forums to become a resource for those people.

You might find the support you seek at the [Kali Forums]("https://forums.kali.org/").

Closed

---

