---
title: "Problems with 9.04 -&gt; 9.10 upgrade (lots of unconfigured packages)"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by mishok13 on 2009-12-16
Hello, everybody.

I'm having troubles with upgrading from karmic to jaunty right now. After running do-release-upgrade everything went fine except for several packages that have been left unconfigured.
Here's the output of running dist-upgrade [http://paste.pocoo.org/show/157331/](http://paste.pocoo.org/show/157331/) [500 lines :)]
Everything starts to break after line 22:
```
"$cachedir" is not exported by the Binfmt::Lib module                                                                        
Can't continue after import errors at /usr/sbin/update-binfmts line 24                                                       
BEGIN failed--compilation aborted at /usr/sbin/update-binfmts line 24.                                                       
dpkg: error processing mono-runtime (--configure):                                                                           
 subprocess installed post-installation script returned error exit status 255
```
This leads to lots of problems later, because many packages are dependant on mono-runtime.
Another problem appears on line 368
```
Setting up doc-base (0.9.3) ...                                                                                                  
Too many arguments for Debian::DocBase::Utils::Inform at /usr/sbin/install-docs line 110, near "$force_reregister_flagfile)"     
Execution of /usr/sbin/install-docs aborted due to compilation errors. 

```
This breaks install of ubuntu-desktop.

So, if anyone has any clues on getting these packages configured or at least removed, don't hesitate to share them.
TIA.

---

### Post by llawwehttam on 2009-12-16
Now this is a good example of why I always do a clean install

---

### Post by tommcd on 2009-12-16
I also always do a clean install of Ubuntu. It is the most fail safe way to avoid problems like this.

You can try to attempt a quick fix:
Open up synaptic package manager, click the reload button to update the repos,  then choose the option to fix broken packages.
If that does not fix it, then try running these commands:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
If that returns errors, you could try:
```

sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade

```
If that does not fix things, you should probably just go ahead with a clean install of 9.10. It will likely be the fastest and easiest way to clean things up. If you have a separate home partition, then all your data will be safe. If you do not have a separate home partition, then this would be a good time to create one.

Welcome to the Ubuntu forums! Sorry your dist-upgrade went awry. Do a clean install and you will be back in business in no time.

---

### Post by mishok13 on 2009-12-16
Yeah, I've tried that (well, the packages are in "not configured" state, not "broken" so trying to fix them would obviously not help). Anyway, thanks for the tips. 
Making a clean install is not a really good way to spend working day, but it seems like I'll have to do it -- having great deal of troubles with X.org and emacs is not productive. :(

Thanks again for the answers.

---

