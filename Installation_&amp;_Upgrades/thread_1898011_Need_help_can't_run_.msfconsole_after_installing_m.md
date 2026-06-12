---
title: "Need help can't run ./msfconsole after installing metasploit on ubuntu 11.10"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by letter2u on 2011-12-20
Hello there, I'm installing metasploit on my machine few hours ago, but after the installation
when I need to run the ./msfconsole on the terminal it said that I don't get the rubygems, but I checked it for sure that I already have the rubygems, so when I try to run the ./msfconsole it show this message

```
/usr/lib/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:36:in `gem_original_require': /opt/metasploit-4.1.4/msf3/lib/msf/core/auxiliary/report.rb:269: syntax error, unexpected ')' (SyntaxError)
	from /usr/lib/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:36:in `require'
	from /opt/metasploit-4.1.4/msf3/lib/msf/core/auxiliary/mixins.rb:11
	from /usr/lib/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:36:in `gem_original_require'
	from /usr/lib/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:36:in `require'
	from /opt/metasploit-4.1.4/msf3/lib/msf/core/auxiliary.rb:15
	from /usr/lib/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:36:in `gem_original_require'
	from /usr/lib/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:36:in `require'
	from /opt/metasploit-4.1.4/msf3/lib/msf/core.rb:51
	from /opt/metasploit-4.1.4/msf3/lib/msf/ui/console/driver.rb:1:in `require'
	from /opt/metasploit-4.1.4/msf3/lib/msf/ui/console/driver.rb:1
	from /opt/metasploit-4.1.4/msf3/lib/msf/ui/console.rb:10:in `require'
	from /opt/metasploit-4.1.4/msf3/lib/msf/ui/console.rb:10
	from /opt/metasploit-4.1.4/msf3/lib/msf/ui.rb:10:in `require'
	from /opt/metasploit-4.1.4/msf3/lib/msf/ui.rb:10
	from ./msfconsole:118:in `require'
	from ./msfconsole:118

```

I'm wondering what's going on with this?

N.B. : Sorry for my bad english translation, and sorry if I put this thread on the wrong place of the forum, but for real I need your help :(

---

### Post by MAFoElffen on 2011-12-20
> **letter2u said:**
> Hello there, I'm installing metasploit on my machine few hours ago, but after the installation
when I need to run the ./msfconsole on the terminal it said that I don't get the rubygems, but I checked it for sure that I already have the rubygems, so when I try to run the ./msfconsole it show this message

```
/usr/lib/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:36:in `gem_original_require': /opt/metasploit-4.1.4/msf3/lib/msf/core/auxiliary/report.rb:269: syntax error, unexpected ')' (SyntaxError)
    from /usr/lib/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:36:in `require'
    from /opt/metasploit-4.1.4/msf3/lib/msf/core/auxiliary/mixins.rb:11
    from /usr/lib/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:36:in `gem_original_require'
    from /usr/lib/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:36:in `require'
    from /opt/metasploit-4.1.4/msf3/lib/msf/core/auxiliary.rb:15
    from /usr/lib/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:36:in `gem_original_require'
    from /usr/lib/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:36:in `require'
    from /opt/metasploit-4.1.4/msf3/lib/msf/core.rb:51
    from /opt/metasploit-4.1.4/msf3/lib/msf/ui/console/driver.rb:1:in `require'
    from /opt/metasploit-4.1.4/msf3/lib/msf/ui/console/driver.rb:1
    from /opt/metasploit-4.1.4/msf3/lib/msf/ui/console.rb:10:in `require'
    from /opt/metasploit-4.1.4/msf3/lib/msf/ui/console.rb:10
    from /opt/metasploit-4.1.4/msf3/lib/msf/ui.rb:10:in `require'
    from /opt/metasploit-4.1.4/msf3/lib/msf/ui.rb:10
    from ./msfconsole:118:in `require'
    from ./msfconsole:118

```I'm wondering what's going on with this?

N.B. : Sorry for my bad english translation, and sorry if I put this thread on the wrong place of the forum, but for real I need your help :(
I read that as what it said: 
Syntax Error, unexpected ")"
Beyond that, I'm not familiar with that specific exploitation/penetration product, so I can't help you on where to look for that.

EDIT-- Where you should probably ask this is on the Rapid7 Community Boards... Where they are familiar with that product and it's installation.

---

### Post by letter2u on 2011-12-22
> **MAFoElffen said:**
> I read that as what it said: 
Syntax Error, unexpected ")"
Beyond that, I'm not familiar with that specific exploitation/penetration product, so I can't help you on where to look for that.

EDIT-- Where you should probably ask this is on the Rapid7 Community Boards... Where they are familiar with that product and it's installation.

Hi MAFoElffen!

thanks for your answer, I'll look there for the answer then :D

---

### Post by Dangertux on 2011-12-22
You need to be running it as root.

---

