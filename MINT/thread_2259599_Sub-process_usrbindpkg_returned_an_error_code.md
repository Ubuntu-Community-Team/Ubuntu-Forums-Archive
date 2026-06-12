---
title: "Sub-process /usr/bin/dpkg returned an error code"
date: 2015-01-05
forum: MINT
---

### Post by snitz2 on 2015-01-05
I'm trying to install Metasploit on LinuxMint 17 but I keep getting this error, and now the update manager disappeared from the taskbar and it won't open if I goto Administration >> Update Manager.

```
halnex@Node ~ $ sudo apt-get autoremove && sudo apt-get clean && sudo apt-get autoclean
[sudo] password for halnex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1382 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up metasploit (4.11.0-2014122301-1kali0) ...
/etc/init.d/metasploit: invalid arguments
 * Starting Metasploit rpc server prosvc                                 [ OK ] 
/etc/init.d/metasploit: invalid arguments
 * Starting Metasploit web server thin                                          /usr/lib/ruby/vendor_ruby/bundler/spec_set.rb:92:in `block in materialize': Could not find rake-10.4.2 in any of the sources (Bundler::GemNotFound)
    from /usr/lib/ruby/vendor_ruby/bundler/spec_set.rb:85:in `map!'
    from /usr/lib/ruby/vendor_ruby/bundler/spec_set.rb:85:in `materialize'
    from /usr/lib/ruby/vendor_ruby/bundler/definition.rb:132:in `specs'
    from /usr/lib/ruby/vendor_ruby/bundler/definition.rb:177:in `specs_for'
    from /usr/lib/ruby/vendor_ruby/bundler/definition.rb:166:in `requested_specs'
    from /usr/lib/ruby/vendor_ruby/bundler/environment.rb:18:in `requested_specs'
    from /usr/lib/ruby/vendor_ruby/bundler/runtime.rb:13:in `setup'
    from /usr/lib/ruby/vendor_ruby/bundler.rb:121:in `setup'
    from /usr/lib/ruby/vendor_ruby/bundler/setup.rb:17:in `<top (required)>'
    from /usr/lib/ruby/2.1.0/rubygems/core_ext/kernel_require.rb:55:in `require'
    from /usr/lib/ruby/2.1.0/rubygems/core_ext/kernel_require.rb:55:in `require'
    from /opt/metasploit/apps/pro/ui/scripts/ctl.rb:30:in `start_thin'
    from /opt/metasploit/apps/pro/ui/scripts/ctl.rb:47:in `<main>'
invoke-rc.d: initscript metasploit, action "start" failed.
dpkg: error processing package metasploit (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 metasploit
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What can I do?

---

### Post by mörgæs on 2015-01-06
This is bad:
```
[COLOR=#000000]*1382 not upgraded*[/COLOR]
```

Please run 
```
sudo apt-get update
sudo apt-get dist-upgrade
```

and post the results in CODE (not QUOTE) tags.

---

