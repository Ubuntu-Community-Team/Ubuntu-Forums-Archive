---
title: "Help with downloading/installing a lightweight ubuntu."
date: 2013-08-04
forum: Installation &amp; Upgrades
---

### Post by john19 on 2013-08-04
Dear Ubuntu forum,
I am a beginner who is deciding to switch my laptop from Puppy Linux, a lightweight distro, to Ubuntu 12.04 LTS so that I can have the same OS that my University uses. 

One thing that I don't like is having a lot of default programs and background services that I never use - the bloat associated with bigger OS's. I'm curious if it would be easier to download the regular 64-bit Ubuntu 12.04 and then delete some programs or if I should start out with the [Ubuntu 12.04 "Precise Pangolin" Minimal CD]("http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/mini.iso") and then use the command "sudo apt-get install" to install the programs I do need one by one. My guess would be that the second would take less time overall, but there would be something important that I would forget to install or some extra technical difficulty would might pop up, but I'm not sure. I'm not exactly sure what I would need to install.

Note that my memory space is pretty limited - I typically use a 2Gb usb as a portable hard drive that contains my OS and all my files - so smallness is a convenience, but so is all-around stability and functionality. Besides the very basic software like a terminal, sound driver, laptop power management, GUI window, laptop touchpad driver, wifi driver, and WiFi network connection tool, the only programs that I plan on using anytime soon are Google Chrome, AbiWord, a plain text editor, the Java Runtime Environment, Adobe Flash, Adobe PDF reader plugin, and Eclipse. I don't even need a log-in manager like gdm - supposedly I can just edit .bash_profile or /etc/inttab and go straight into the genome-shell GUI without needing to see the log in screen.

One thing that I do to increase the battery life (by like 40%) and cut disk use on my laptop is I boot Puppy Linux into RAM or I boot the live media and put everything in the default RAM Disk (my laptop is getting upgraded from 4Gb of RAM to 8Gb of RAM, so RAM has got room). I know that Ubuntu doesn't boot into RAM like Puppy, but it does have a live CD. Can I use the Ubuntu live CD as a full fledged, fully functional minimal OS the way I use the Puppy Live CD? Also, can I get or make a minimalist live media version of the Ubuntu live CD - just like the official live CD version but with a lot less things preinstalled?

What's the best way for me to go about making the transition from Puppy Live Media to Ubuntu 12.04?

---

### Post by Warren Hill on 2013-08-04
You are asking about 12.04LTS so why would you want the 12.10 download?

I'd recommend you start minimal then add what you want; Instructions and download here:

[h=1][[SIZE=4]Installation/[/SIZE]]("https://help.ubuntu.com/community/Installation/MinimalCD")[SIZE=4][MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD?action=fullsearch&value=linkto%3A%22Installation%2FMinimalCD%22&context=180")[/SIZE][/h]

---

### Post by john19 on 2013-08-04
Sorry, I meant to copy and paste "[Ubuntu 12.04 "Precise Pangolin" Minimal CD]("http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-amd64/current/images/netboot/mini.iso")", not "[Ubuntu 12.10 "Quantal Quetzal" Minimal CD]("http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-amd64/current/images/netboot/mini.iso")", which was just one over from it.

---

### Post by john19 on 2013-08-04
Can I run the minimal CD with all the additional programs and features I want entirely in RAM, without a hard disk install? Or will I have to install the CD contents to hard drive and restart the computer before getting to use the GUI? Because I got the impression that the latter was true - that I had to install to hard disk and restart everything and boot from hard disk before I can get all my Windowed programs and the GUI fully running. See: [http://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24](http://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24) .

If no one replies my assumption will be that I don't have to install the minimal CD to a hard drive and I can just download everything from the minimal CD and run it without restarting the computer.

---

### Post by ibjsb4 on 2013-08-04
That link (instructions) leave a lot to be desired.

If you want an Ubuntu that will run off CD then try [Lubuntu]("http://www.lubuntu.net/") or [Xubuntu]("http://xubuntu.org/").

Trying to build your own is not a easy as that link makes it sound (I built mine), there is more to it.

You could also try [Puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm"), it will run in ram and can run ubuntu software.

---

### Post by john19 on 2013-08-04
Your post: "You could also try [Puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm"), it will run in ram and can run ubuntu software."

My Post: "I am a beginner who is deciding to switch my laptop from [Puppy Linux]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm"), a  lightweight distro, to Ubuntu 12.04 LTS so that I can have the same OS  that my University uses." 

Anyway, so you're saying that I'll probably run into technical difficulties if I try to make my own lightweight Ubuntu and that it would be wiser for me to use a pre-built CD instead. If making my own lightweight Ubuntu will take me more than 8 hour's time total, including any technical difficulties that arise, then you're probably right that it's probably not worth the effort (although 3-5 hours would be okay). The full Ubuntu Live CD is 650MB - I mean that's not too bad if I have 8Gb of ram. I mean I should have 7Gb left over, which is plenty for writing code and watching Youtube. I'll probably try the official live CD ( [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) ) for the long term support version of Ubuntu over a smaller "non-official" live CD version like Lubuntu.

Note, I did not realize the following was the case until just now: "The 30MB minimal ISO mini.iso is NOT a minimal Live-CD" [http://askubuntu.com/questions/142413/how-to-build-my-custom-ubuntu-using-minimal-cd](http://askubuntu.com/questions/142413/how-to-build-my-custom-ubuntu-using-minimal-cd).

---

### Post by ibjsb4 on 2013-08-04
Oops


Ok, do a terminal only install with the mini cd and then ..
```
sudo apt-get install --no-install-recommends gnome-session-fallback nautilus && sudo apt-get install lightdm synaptic gnome-terminal firefox
```

And with a reboot your off and running, but still missing a lot of crap :)

Let us know what else you need

---

### Post by Cheesemill on 2013-08-04
> **john19 said:**
> Note that my memory space is pretty limited - I typically use a 2Gb usb as a portable hard drive that contains my OS and all my files

This is going to be an issue.

Even just a Ubuntu Mini CD installation takes around 1.5GB and that's just for a command line system.

You'll never be able to install a GUI and applications and stay comfortably under 2GB.

---

### Post by john19 on 2013-08-04
"Even just a Ubuntu Mini CD installation takes around 1.5GB and that's just for a command line system."
Wut??? But I thought the fully functional Ubuntu live CD that comes with everything I need plus the GUI - I thought that took up less than 1Gb. And my current OS plus all my programs (Java, my IDE, flash, web browser, GUI, GNome music player, abiword, Gnumeric spreadsheet, network connection, etc.) is just 900Mb total. 

Recently I have basically been leaving my laptop on 24/7, using RAM "sleep mode" instead of hibernate because I've been using the Puppy Live Media in "pfix=ram" mode full time, so I was thinking it might be convenient to ditch the full install and only use the live media the way I do with Puppy Linux. No hard drive, no disk drive except for booting.

I'm thinking that the live CD may be more space efficient than the full download. The live CD .iso is pretty small and roughly matched up to the actual size of the OS download. Like the compressed "squash system file" on my OS is like 125Mb, the uncompressed folder is 250Mb, and the live CD .iso is about 160Mb. So I was thinking that the Ubuntu live CD .iso file should behave similarly in terms of space - like since the live CD .iso takes up 700Mb of space, it should (please correct me if I'm wrong) take up roughly 1 Gb of space on hard drive or on RAM if you don't add any features that don't already come with the live CD. Like I don't actually need to do an install to an internal hard drive and I wonder if the live CD is relatively space efficient and low on battery consumption (like can you just take out the live CD after booting and go with no hard drive or CD drive the way you can with the puppy live media on "pfix=ram" mode?).      

For the terminal install, If I did install to USB, I was thinking something similar to the above. I was thinking a little more like:
"sudo apt-get install gnome-shell nautilus && sudo apt-get install lightdm synaptic gnome-terminal firefox network-manager"

because the gnome-shell has full GUI functionality and only takes up 40Mb more than gnome-session-fallback. Also, I need the network manager to connect to wifi.
Also, a lot of the "--no-install-recommends" programs are stuff that is important but that doesn't take up a lot of space, 
and also some people have major technical difficulties with "--no-install-recommends" like inability to boot. See:
[http://askubuntu.com/questions/65081/implications-of-no-install-recommends-apt-get-install](http://askubuntu.com/questions/65081/implications-of-no-install-recommends-apt-get-install) . But what the above guy said about no GUI taking up
1.5Gb makes that more functional USB install seem implausible.

---

### Post by 1clue on 2013-08-04
John19,

Is there a reason for the 2g limit?  I know it's the size of your USB stick, but is it possible to get a bigger stick?

There are a couple reasons for asking.  First, that's pretty cramped.  Second, a stick that small is probably USB1 (just a guess) which is going to be really, really slow.

---

### Post by john19 on 2013-08-04
Well, it's the only stick I currently own. I guess I could buy a bigger one in the future, but currently, my laptop has no USB stick, CD drive, or hard disk. It's in Puppy "pfix=ram" mode, meaning that absolutely everything is booted to and stored in RAM. If I shut my laptop off now without saving my session to a USB stick or CD session, literally everything would be wiped. The battery lasts about 40% longer this way and Netbeans opens in 5 seconds instead of 20. Instead of shut down, I usually use sleep mode. So I don't see the need for any USB of any size, even 2Gb. If I have something important that needs backing up, I can just save to Google Drive or transfer it to my university's server using Filezilla or scp. That's why I keep asking about and mentioning the Ubuntu Live CD - to use it as a long term alternative to the install. Like I don't need a swap partition or USB partition - I have 8 Gb of RAM and don't use my laptop for storing things like songs, photos, or videos.

---

### Post by 1clue on 2013-08-05
Ya I get the running-from-RAM thing, I think that's cool but can't really believe that you'd install everything from the live CD session every time you boot.  You must have almost nothing in there aside of normal tools.

I've tried booting a stock Xubuntu install from a usb stick, and it takes forever.  Not the same as what you're doing, but just a data point for you.  You definitely want the smallest operating system image you can get, you would definitely want a compressed image but I think you should get a bigger stick if you're graduating up to something that uses persistent storage.

---

### Post by john19 on 2013-08-05
Yeah, I don't turn my laptop off anymore - just sleep mode. The Ubuntu live CD seems like the easiest and quickest thing, at least compared to the minimal CD thing or the full install. I can shut it down once every six months.

---

### Post by 1clue on 2013-08-06
Yeah I got all that, I'm just thinking of how many more hardware failures I've had compared to you.

You know, if you're trying to prove something you've done it.  If you want something practical, then maybe you should consider persistent storage of some sort.

---

