---
title: "Xubuntu xfce un-install /  install"
date: 2014-08-31
forum: Installation &amp; Upgrades
---

### Post by gordon99 on 2014-08-31
I am running on Xubuntu Xfce 14.04. 
I am having difficulty installing Seahorse because of unnmet dependencies. I understand Seahorse is automatically included with Xubuntu so I may have corrupted the package somehow. I was contemplating removing Xubuntu Xfce and then re-installing it but it has been suggested that overwriting would be as effective in getting the OS/desktop package back to how it should be.
Could someone please show the commands I must use to get back to unspoilt Xubuntu Xfce please.

---

### Post by vasa1 on 2014-08-31
> **gordon99 said:**
> I am running on Xubuntu Xfce 14.04. 
I am having difficulty installing Seahorse because of unnmet dependencies. I understand Seahorse is automatically included with Xubuntu ...
According to [this link]("http://packages.ubuntu.com/trusty/xubuntu-desktop"), Seahorse is **not** part of Xubuntu. It is a component [of Ubuntu]("http://packages.ubuntu.com/trusty/ubuntu-desktop").

You can get an idea of which flavors include Seahorse by running **apt-cache show seahorse** and looking for what's listed at the bottom in **Tasks**:```
Task: ubuntu-desktop, ubuntu-usb, edubuntu-desktop, edubuntu-usb, ubuntu-gnome-desktop

```

---

### Post by fidelis2 on 2014-08-31
> **vasa1 said:**
> According to [this link]("http://packages.ubuntu.com/trusty/xubuntu-desktop"), Seahorse is **not** part of Xubuntu.
Yes, that's why I had to install it via software center -- searching for "seahorse" and then installing it.
Since then it works on my Xubuntu 14.

Has the original poster also re-installed seahorse?

When I encounter such re-installation problems (usually only for manually dpkm'ed ones like when I upgraded from Openoffice 4.10 to 4.11) I always use the package "synaptic" because there you see all the matching packages and you can "completely un-install" them.
But for OO this wasn't enough; so after using synaptic to un-install the old OO, I left synaptic and did all the apt-get purge, autoremove etc. steps to completely remove the old packages from hard-drive. (Another way would be to use the Bleachbit GUI to clean the old package)
Only then the re-install of the OO packages worked.

Maybe the original poster would need to apt-get purge, autoclean etc. his system, too?

---

### Post by Dennis N on 2014-08-31
> According to this link, Seahorse is not part of Xubuntu. 

Exactly so:

From Xubuntu 14.04:

```
dmn@Sydney:~$ apt-cache policy seahorse
seahorse:
  Installed: (none)
  Candidate: 3.10.2-0ubuntu1
  Version table:
     3.10.2-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

Did you install XFCE desktop environment into an existing Ubuntu? If so, Ubuntu is where Seahorse came from. Seahorse is described as the "GNOME front end for GnuPG." There is (at least in my Ubuntu 12.04) a seahorse plugin for Nautilus that is used to encrypt documents.

---

### Post by vasa1 on 2014-08-31
> **Dennis N said:**
> ...

Did you install XFCE desktop environment into an existing Ubuntu? ...
That is the impression I got from [here]("http://ubuntuforums.org/showthread.php?t=2239060&p=13098735#post13098735").

---

### Post by gordon99 on 2014-08-31
Clearly, I am chasing my own tale, so back to basics: My objective is to stop Evolution requiring my email passwords each time I enter its portals. If I can stop being asked for 'Keyring' passwords at various other times that would be a bonus. I understood from fidelis2 that an essential first step was to install Seahorse from the software centre. When I tried to do just that it did not work because I had "unmet dependencies". I then tried, maybe using the wrong command syntax, to install Seahorse via Terminal. That did not work either because of  something about 'gcr' . I thought vasa1 was hinting that Seahorse should have installed automatically with Xubuntu but I now realize it was with Ubuntu. I may well have removed Ubuntu before installing Xubuntu but, though I just cannot remember, it seems I probably did. 
Nevertheless, fidelis2  thinks I need Seahorse and says it installed ok for him in Xubuntu 14 Xfce.  As it won't install for me I can only assume I have corrupted the OS and therefore need to overwrite (or remove and re-install) it. Hence my request for guidance in the commands to do just that.

---

### Post by gordon99 on 2014-08-31
Well, I think I am almost there. I thought I would see if, what I took to be the broken package "gcr 3.9.1", would install from Terminal and much to my surprise a large number of lines downloaded with no error message at the end. I returned to desktop to access the software centre but found it would not open. In fact the software centre icon had changed. I took the only action I could think of which was to install the software centre from scratch. Luckily that worked. I then tried to install "Password and keys" from the Centre and this time that also worked. After then juggling with 'password and keys' in Settings, I was able to access my emails without having to enter email account passwords after, that is,  having done it just once to set  them up. The only thing Evolution it is still requiring is my OS log-in PW but I feel fairly sure I will find my way around that. Thank you all for your interest and help.

---

### Post by ian-weisser on 2014-08-31
> **gordon99 said:**
> The only thing Evolution it is still requiring is my OS log-in PW but I feel fairly sure I will find my way around that. Thank you all for your interest and help.

Do you use auto-login?
I don't recall you mentioning that in either thread.
I should have noticed - it's important.
If you do use auto-login, then I'm afraid Evolution will always require your login password. Your login password, or some other form of authentication, is necessary to unlock the keyring.

If you login with a password, your login usually unlocks the keyring - you have proven to the system's satisfaction that you are really you an have a right to all the stored keys.

If you use auto-login, the keyring remains locked until you prove yourself to the system...usually by entering your login password.

It can be more complicated than that: login and keyring passwords can be different, etc.

---

### Post by gordon99 on 2014-09-01
I log on to Xubuntu with a password (I assume auto log-in gets you into Xubuntu without having to give a password).  I have set up keyring with the same PW that I use to log on to xubuntu.  When I went onto Evolution today I was required to enter the password. However, after leaving Evolution and returning later, not having closed down the laptop, I was able to get onto my emails without having to insert my PW. From what you say, Ian, I understand it should be possible to tweak the settings so that I have to enter my password when logging on to xubuntu only and this should unlock the keyring also. I will see what I can do. Thanks for your observations.

---

