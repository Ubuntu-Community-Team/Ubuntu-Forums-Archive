---
title: "stuck dpgk"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by chejose on 2010-09-25
In a trip to the USA I recently brought back a Lenovo s12. Everything has been OK until now. I explain:

I attempted to install the Ubuntu-restricted-extras package. It went fine until it reached downloading from sourceforge.net. There it stuck.

 What it did was cycle through a series of "connecting to ____.dl.sourceforge.net. In the blank space came a series of 9 words: switch, mesh, dfa, heanet, jaist, etc. and each time it was timeout. It repeated thw ame list and apparently it would continue cycling forever.

So the only way to kill it was to shut down. But now I cannot install any packages. And a "sudo apt-get update" gets an answer that dpkg has been interrupted.

So, according to instructions, I run "sudo dpkg --configure -a" And it goes back to trying to download from sourceforge.net. And it just cycles through the same 9 files/fonts/?

In other words, dpkg is broken because it cannot finish with sourceforge.net. 

So how in the world can I get myself out of this situation?

Thanks for help,

José

---

### Post by lykeion on 2010-09-25
What instructions? Any links to them?

Your sources.list may have some strange entries in it. Could you paste the output of this command:
```
cat /etc/apt/sources.list
```

EDIT: 
If you try to install the ubuntu-restricted-extras there's a simple solution here (just install it with a click):

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by sikander3786 on 2010-09-25
> **lykeion said:**
> What instructions? Any links to them?

Your sources.list may have some strange entries in it. Could you paste the output of this command:
```
cat /etc/apt/sources.list
```

EDIT: 
If you try to install the ubuntu-restricted-extras there's a simple solution here (just install it with a click):

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
He will not be able to install any software from any source or manager either Software Center or Synaptic or Aptitude until the broken package is configured properly.

To the OP: Please post the exact message returned by

```

sudo apt-get update

```

from a terminal.

---

### Post by chejose on 2010-09-25
Sorry, Started to answer but am not ready yet... and I can't close this. So will come back a bit later.

José

---

### Post by chejose on 2010-09-25
Sikand

I was on the wrong machine before. I ran apt-get update as you suggested. The result is a bit long, and the end is the "problem. I will post it in any case:

Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

So this is where I started.

Jose

---

### Post by chejose on 2010-09-25
Here is the result of "dpkg --configure -a

Setting up ttf-mscorefonts-installer (3.2) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--2010-09-25 13:33:12--  [http://downloads.sourceforge.net/core](http://downloads.sourceforge.net/core) fonts/andale32.exe
Resolving downloads.sourceforge.net... 1.0.0.0
Connecting to downloads.sourceforge.net|1.0.0.0|:80... 

From here it continues trying to download files from sourceforge and as I indicated in my first post, it will cycle forever.

José

---

### Post by davidmohammed on 2010-09-25
Hi there,
  this may be your [bug]("https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/464422") ... there seems to be several suggested workarounds - have a read - post #60 may fix your issue.

---

### Post by chejose on 2010-09-25
OK... I took the obvious route. I simply unistalled the ttf-mscorefonts item from synaptic. With that I could run "dpkg --configure -a" with no problems.

Thanks for the help.

José

---

### Post by saviouz on 2011-09-25
> **chejose said:**
> OK... I took the obvious route. I simply unistalled the ttf-mscorefonts item from synaptic. With that I could run "dpkg --configure -a" with no problems.

Thanks for the help.

José

Can you explain me just how to do that? I have the exact same problem

---

### Post by sffvba[e0rt on 2011-09-25
> **saviouz said:**
> Can you explain me just how to do that? I have the exact same problem

Hi,

May I suggest starting a new thread explaining your problem in more detail.  Continuing old threads like this just ultimately leads to confusion on the part of people trying to help.

Thread closed...


Regards
404

---

