---
title: "Trying to install postgres gem"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by AdamKinmont on 2008-07-08
I've been following this guide [http://blog.metasploit.com/2006/09/metasploit-30-automated-exploitation.html](http://blog.metasploit.com/2006/09/metasploit-30-automated-exploitation.html) trying to get autopwn working with metasploit but I came to hang up when I tried to install post gres and got this. 

lumos@Argonth:~$ sudo gem install postgres
Need to update 43 gems from [http://gems.rubyforge.org](http://gems.rubyforge.org)
...........................................
complete
Building native extensions.  This could take a while...
ERROR:  While executing gem ... (Gem::Installer::ExtensionBuildError)
    ERROR: Failed to build gem native extension.

ruby extconf.rb install postgres
extconf.rb:46:in `require': no such file to load -- mkmf (LoadError)
	from extconf.rb:46


Gem files will remain installed in /var/lib/gems/1.8/gems/postgres-0.7.9.2008.01.28 for inspection.
Results logged to /var/lib/gems/1.8/gems/postgres-0.7.9.2008.01.28/ext/gem_make.out

Thanks for any help

---

### Post by Partyboi2 on 2008-07-09
have you got ruby1.8-dev package installed? You also might need build-essential as well
```
sudo apt-get install ruby1.8-dev build-essential
```

---

### Post by AdamKinmont on 2008-07-27
I didn't have ruby dev but I've got it now and the command worked thanks a bunch!

---

