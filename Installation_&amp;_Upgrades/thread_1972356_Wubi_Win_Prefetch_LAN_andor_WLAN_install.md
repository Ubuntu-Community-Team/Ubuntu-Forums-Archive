---
title: "Wubi Win Prefetch LAN and/or WLAN install"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by FoZFoRiC on 2012-05-03
**Wubi Win Prefetch LAN and/or WLAN**             
                                                                Ubuntu desktop 12.04 (several install paths tried)

I have a second laptop that the cd/dvd drive has gone out on and does  not support boot from USB stick.  I decided to try the windows installer  for wubi, but after restart it has hung up in so many points I am  unsure just what is going on.  
I think it is because it has to install the broadcom WLAN drivers from  remote, but there is no way for it to connect.  The laptop has a LAN  connection as well (and all of the hardware still works on the winOS on  the laptop) but I can not tell if wubi can find the LAN as the install  and/or recovery boot options tell me to handle the broadcom issues and  then hangs instead of allowing me to work on the LAN issues. 
As I said this has hung in so many places its spinning my head, the only  repeating instance is the broadcom drivers which I understand how I am  supposed to fix that but can't because i can not get through enough to  resolve the LAN issues.

**(QUESTION) Is there a way to have the windows installer portion of wubi  prefetch the LAN or WLAN drivers?  (OR) can I access the ubunti files  from windows and have it compile needed files on startup of ubuntu?  (which sounds like a security risk if its possible, that is why I  haven't already tried it)**

---

### Post by FoZFoRiC on 2012-05-03
Quoting from the wubi wiki guide:

[I]**"How do I install Wubi on a machine with no Internet connection?**

 Wubi also works with physical Ubuntu Desktop Live CDs. Wubi.exe is available in the root folder of the CD. [/I] [I]
If  you do not have a CD, try to find a computer with Internet access, and  download both Wubi.exe and the required Desktop ISO from the same  location (the release has to match): 

Copy both files into the same folder on the machine with no Internet access and run the Wubi executable. "[/I] 

**This doesn't work since the braodcom drivers have to be accessed after install because they can not be included in the package.  Just trying to further Illustrate what my problem is.**

---

### Post by critin on 2012-05-03
Do you use a router?  If you can plug ethernet wires directly to both laptops during the install, it would work.

---

### Post by FoZFoRiC on 2012-05-03
> **critin said:**
> Do you use a router?  If you can plug ethernet wires directly to both laptops during the install, it would work.

huh? are you suggesting setting up my 1st laptop as a file server?

---

### Post by critin on 2012-05-03
No, a wired lan is stronger than a wireless and the drivers are there.  Go wireless again after the install is done.

---

### Post by FoZFoRiC on 2012-05-03
> **critin said:**
> No, a wired lan is stronger than a wireless and the drivers are there.  Go wireless again after the install is done.


yea, that is what I am trying to do. but it hangs trying to tell me to resolve the broadcom issues and I can not get it to find/ install the wired LAN adapter and proceed.

---

### Post by FoZFoRiC on 2012-05-03
[SIZE=4]It would make so much more sense if in this step;[/SIZE]


[IMG]https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=wubi-123.png[/IMG]


[SIZE=4]It would allow you to set up your LAN specific and/or WLAN specific hardware drivers and protocols.

but instead, "there is no three"
[/SIZE]

---

### Post by critin on 2012-05-03
8.04 is too old and you won't be able to get updates easily even if it was installed directly to a HD.  I suggest 10.04.
Wubi is installed directly into Windows and uses its drivers.  I wouldn't think you'd have to install lan drivers.  Installing Wubi remotely though is something I haven't done.

I still believe if both machines were wired there shouldn't be a problem with lan drivers.  You would simply copy the files over to the target machine and install the OS.

You do have the windows machines already set up as a lan/wlan network don't you?
Of course you do or you couldn't have copied the files over--sorry, just thinking out loud.

---

### Post by critin on 2012-05-03
A thought..Are you trying to** install from** the machine that has internet?  Or did you **MOVE the wubi file** to the target and trying to install it there?

---

### Post by FoZFoRiC on 2012-05-03
im using 12.04 desktop, that graphic is just from the [wubi guide]("https://wiki.ubuntu.com/WubiGuide")

everything is setup on and running fine as windows computers/networks are concerned. 

I don't see any indication that wubi uses anything from the windows OS portion of its install.  if it does, I am now wondering if it somehow captured the settings from a VPN that appears first in my list of network connections in windows.  Wonder how it determines which network adapter is the one it will use during any get processes during the install.  
All this wondering is just making me think they need to allow you to review the LAN settings in the initial setup before reboot.

I guess I need to just ask 'how do you install a LAN network adapter from the recovery console'.  because that is the only  command line I can get to.

---

### Post by critin on 2012-05-03
Wubi is a Windows app.  Like Word.  It is installed inside windows on a small section of the Windows partition and uses the same hardware.  
If you have the iso (moved over from the other machine) on the machine, why not just install that without using Wubi?  Using the ethernet wire and the copy of the iso will let you install on its own partition without worrying about the lan.

---

### Post by critin on 2012-05-03
> QUESTION) Is there a way to have the windows installer portion of  wubi  prefetch the LAN or WLAN drivers?  (OR) can I access the ubunti  files  from windows and have it compile needed files on startup of  ubuntu?  (which sounds like a security risk if its possible, that is why  I  haven't already tried it)

I really don't understand why you'd need the lan drivers at this point if the lan network is already set up.  OS's are added to a home network after installing if the user chooses to do so.  At least mine are.

I have lots of iso's on one computer and when I want one, I use my lan network to choose one to move and install on another machine.  

This is a new issue for me and I hope to learn from it.  :KS

---

### Post by FoZFoRiC on 2012-05-03
> **critin said:**
> Wubi is a Windows app.  Like Word.  It is installed inside windows on a small section of the Windows partition and uses the same hardware.  
If you have the iso (moved over from the other machine) on the machine, why not just install that without using Wubi?  Using the ethernet wire and the copy of the iso will let you install on its own partition without worrying about the lan.

Well, first off, the wubi on the iso just tells you to reboot and run from the cd.  which won't happen because the cd drive doesn't work.  
Then, just because a program is installed on windows doesn't mean it can access the hardware, that's what drivers are for. 
Also the wubi that you download separately (and is the only wubi that installs on windows) is different from the one on the iso. The wubi guide does say place the iso in the same directory as the net wubi, but it doesn't install the WLAN adapters specifically because broadcom won't let them put them in the package (but it should still be acceptable for wubi to  run the b43-fwcutter before restart but it doesn't). 
I don't think it does any setup before restart other than setting an account and downloading the remaining files from the iso because of this.
I keep mentioning the WLAN _ONLY_ because the system hangs telling me to go to a [website]("http://wireless.kernel.org/en/users/Drivers/b43") to fix it and then I cant work on the LAN problem any more.  
I am still trying to get the LAN to work from the recovery console

---

### Post by critin on 2012-05-03
> Well, first off, the wubi on the iso just tells you to reboot and run  from the cd.  which won't happen because the cd drive doesn't work.  

Yes, my mistake.  I knew that and forgot, sorry.

---

### Post by FoZFoRiC on 2012-05-03
[SIZE=4]ugh, why doesn't the win wubi have this accessibility feature?

[/SIZE]Quote:
                                                 1. Boot to the live CD/USB
 2. When the screen comes up showing the accessibility icon (little  stick  man and keyboard at the bottom of the screen), press any key
 3. Pick your language, press enter
 4. Press F6, this will launch a dialogue
 5. Press esc to get rid of the dialogue
 6. You should now have a cursor from which you can enter commands below the boot options: Type       Quote:
                                                 b43.blacklist=yes                                 
  making sure there is a space before and after the text you enter.
 7. Press enter to either 'Try Ubuntu without installing' or 'Install Ubuntu'

---

### Post by FoZFoRiC on 2012-05-03
[SIZE=3]Well this link someone at askubuntu helps. just figuring out whether I can just swap NOMODESET for b43.blacklist=yes or if I have to format it as a command[/SIZE]

[http://ubuntuforums.org/showpost.php?p=10089820&postcount=8](http://ubuntuforums.org/showpost.php?p=10089820&postcount=8)

---

### Post by FoZFoRiC on 2012-05-03
[SIZE=3]well here goes nothing, started the whole thing over and added the blacklist line in the wubildr-disk.cfg [/SIZE]

Apparently this appeared on someone's blog or something, but it doesn't reference the cfg i edited 

[http://linux-software-news-tutorials.blogspot.co.uk/2012/04/installing-ubuntu-1204-crashes-because.html](http://linux-software-news-tutorials.blogspot.co.uk/2012/04/installing-ubuntu-1204-crashes-because.html)

---

### Post by FoZFoRiC on 2012-05-03
damn, nothing .... locked up even faster with some kind of kernel panic... 

kernel panic not syncing vfs not able to mount root
then 10 lines of something and 
locks up on kernel thread help

or something like that...



[COLOR=Red]SCUMBAG BROADCOM[/COLOR]

---

### Post by FoZFoRiC on 2012-05-04
[SIZE=3]That's it. I'm done.  I went ahead and tried everything on my 3rd laptop that is identical to the 2nd and couldn't get it to work at all.
Even tried the natty narwhal 11.10 that is packaged as ultimate edition, because I couldn't find the previous release on Ubuntu's site, and that had all the same issues.
I'm just going to put these laptops on the incompatible hardware list.
Funny thing though, linuxmint runs like a charm.[/SIZE]

---

