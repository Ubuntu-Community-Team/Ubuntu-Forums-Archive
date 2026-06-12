---
title: "Synaptic/Aptitude/Apt-get not working"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by arachnegl on 2007-07-25
Hi there,

I have managed to get an error I didn't think was possible.

I was installing 'secondlife-install' with gdebi using a package downloaded from getdeb. This installation was interrupted. 

'secondlife-install' basically downloads another huge file (I don't know from where it sources it...) and then that completes the installation.

Now none of my apt based installers work because they come across this half-installed package. When I try to remove, reinstall, ignore it, APT refuses. Basically I can't upgrade or install anything.

error message from update manager: (same error under apt-get)
'Unknown Error: '<type 'exceptions.SystemError'>' (E:The package secondlife-install needs to be reinstalled, but i can't find an archive for it.)'

It is flagged up as H under Aptitude

How can I make my APT healthy again?

Any help greatly appreciated!! I don't want to have to reinstall all over again...
Thanks!!

---

### Post by Pumalite on 2007-07-25
Try: sudo dpkg --configure -a

---

### Post by arachnegl on 2007-07-25
Already tried that and it doesn't work. 

It gives this one-liner:
dpkg: status database area is locked by another process

A guess as to what process that might be is the gdebi package installer. This is what I originally used to install the package off the getdeb website.

---

### Post by Pumalite on 2007-07-25
Then try this: sudo dpkg --configure -a && sudo apt-get -f install

---

### Post by arachnegl on 2007-07-25
Thanks for your suggestions so far!

that same error reply just keeps on coming back....  I have also tried 'sudo aptitude clean'

It seems to my novice mind that the whole APT/dpkg tools are down because of this corrupted process. Is there some kind of 'todo installation file' or location where I can just delete this offending package?

---

### Post by Pumalite on 2007-07-25
You could try downloading it from the Web and installing it by yourself. That would solve the problem. ( I mean the package that got interrupted )

---

### Post by arachnegl on 2007-07-25
I wanted to do that, but can't find where it is sourced... Besides I would be interested to resolve this without capitulating to the demands of the error. 

There must be a way of just deleting the requirement on some database or file somewhere. As an interrupted installation, it has not corrupted my computer or other packages at all.

---

### Post by arachnegl on 2007-07-25
Here is the error that synaptic gives when I try to launch it:

E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by Pumalite on 2007-07-25
Unfortunately I don't have an answer to what you want. Maybe someone that knows better will jump in. The way I got around it for a while ( until I installed the package ) was to use Synaptic and every time it got stuck I would open 'details' which is a dialog window where the program will ask you 'yes' 'no' answers and that way you can continue installing without solving the problem per se. Good luck.

---

### Post by arachnegl on 2007-07-26
the problem is that synaptic won't even run... thanks a lot for your help though!! :)

Anyone else got any ideas?

---

### Post by Seisen on 2007-07-26
Here is the link for secondlife to download the .deb file

[http://www.getdeb.net/release.php?id=1057]("http://www.getdeb.net/release.php?id=1057")

After it downloads put this in the terminal

```
sudo dpkg -i secondlife-install_1.17.0.12-1~getdeb1_i386.deb
``` and hopefully that should reinstall the file.

---

### Post by tjmoes on 2007-07-26
I have the pkg installer not letting me install innotek virtualbox says  only one software management tool is allowed to run at the same time says to close all other pkg installers like updater but updater has no way to close from desktop
:confused:

---

### Post by Seisen on 2007-07-26
Do you have synaptic open or are you dpkg, apt-get or aptitude right now?

---

### Post by tjmoes on 2007-07-26
only thing open is the update mangr icon on panel  which is not updating my files which wants me to 'dpkg' and i have not not used dpkg b4

---

### Post by Seisen on 2007-07-26
Does this have anything to do with this problem?

[http://ubuntuforums.org/showthread.php?t=510266]("http://ubuntuforums.org/showthread.php?t=510266")

---

### Post by tjmoes on 2007-07-26
not really but I just cant instll anything it seems

---

### Post by tommybutu on 2007-07-26
I've had the same problem for two weeks and have tried all suggestions I've come across in this forum. I agree with you it must be possible to eliminate the 'hook' that is creating this error, but no one seems to have any idea about that.
if you find an answer please post it and I shall do the same. Good luck.

---

### Post by tommybutu on 2007-07-26
I should also say that I have tried every suggestion I found on Google but nothing has worked.

---

### Post by anothermikemiller on 2008-01-14
I had the same problem, but for me I had a badly installed package running as a daemon.  I couldn't access the deamon because the client hadn't been installed yet!  I finally got it removed by using the force options under dpkg.  I had to use both --force-hold and --force-remove-reinstreq with the --purge option.  This is the "completely remove this package" option, but aptitude was hung up on a hold flag because the package was corrupted.
This let aptitude stop the daemon and the the modprobes that were started (and broken) and finally uninstall the package.
I turned right around and reinstalled it and my aptitude is working again (and my software works).

Here's the code I used and the dpkg messages:

```

user:~$ sudo dpkg --purge --force-remove-reinstreq --force-hold cdemu-daemon
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... ^[[A136268 files and directories currently installed.)
Removing cdemu-daemon ...
 * Stopping CDEmu userspace daemon                                               * Stopping cdemud daemon...                                             [ OK ] 
 * Removing kernel module (vhba)...                                      [ OK ] 
                                                                         [ OK ]
Purging configuration files for cdemu-daemon ...
user:~$

```

This seems like a really big aptitude bug and we should probably report this to the maintainers.

---

