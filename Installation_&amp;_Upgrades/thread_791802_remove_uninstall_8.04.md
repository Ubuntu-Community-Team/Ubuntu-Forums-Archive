---
title: "remove/ uninstall 8.04"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by tardiaf on 2008-05-12
i just updated to ubuntu 8.04 and do not want it anymore. how do i go back to feisty fawn? i want my comp to be back to normal, im not liking this recent update. can someone please help me?

---

### Post by dje on 2008-05-12
I'm sorry to say that unless you made a backup of feisty you cannot go back to it without a fresh reinstall

dje

---

### Post by tardiaf on 2008-05-12
well i guess im cool with a fresh reinstall... how do i do that now? ill just back up everythin i got now. for the most part its just movies and pictures, an some homework. so its nothing too crazy. can i get some guidelines?

---

### Post by dje on 2008-05-12
Just make sure you backup all your important files, a good way of backing up personal settings as well as files is to use the following in a terminal:
```
sudo tar cvpzf /path/to/backup/destination/home_backup.tgz /home
```
Where /path/to/backup/destination/home_backup.tgz could be /media/usbdisk etc. any destination which isn't on your internal hard drive

Then use your feisty live/alternate install cd to install feisty over hardy ie. install feisty as you did the very first time you installed it

hope that helps,
dje

---

### Post by tardiaf on 2008-05-13
8.04 is so crappy - why the hell did they even release this crap. im pist now.  my comp was doin awesome an now its all buggy from this new release. im so fed up with this bull

---

### Post by skiamakhe on 2008-05-13
Do you want some cheese with that whine? Cut the developers some slack. They bust their butts daily to provide us with one of the best linux distros for *FREE*, with new major releases *EVERY 6 MONTHS*. They can't be expected to anticipate every custom hardware/software combination out there. If you are having problems with your install, how about doing a little research and contribute  some feedback to the community instead of just complaining about it?

Since you are going to reinstall fresh anyway, try 8.04 on a fresh install. Maybe you had some custom packages that the upgrade didn't like.

---

### Post by forestpixie on 2008-05-13
> Do you want some cheese with that whine?:lolflag:

---

### Post by tardiaf on 2008-05-13
id love some cheese wit this wine you comp nerd. i understan they bust their balls, but it seems like they rush to get it out when they can take some more time. but thats my two cents. other than that, i dont know how to do all that fresh install an partition stuff, a buddy of mine built this comp for me an i do my best by researchin how to fix things an get help. other than that, installs an stuff is not my cup a tee an don wanna break this beautiful piece of hardware

---

### Post by skiamakhe on 2008-05-14
Well, you are in luck, because ubuntu is just about the the easiest linux distro out there. If you don't have it already, go to [www.ubuntu.com](www.ubuntu.com) and download the 8.04 desktop version for a standard computer (I'm guessing you don't have a 64-bit proc). What you will get is an .iso file, which is a bit-level image of a CD. You can burn that image from within your current installation of ubuntu. **_[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)_**

Follow the instructions in this thread for backing up your home directory, which will contain all your files, unless you put them someplace weird. If you need help with that, let me know.

Once you've backed things up, boot from the CD you burned, and follow the instructions. When it asks you how you want to partition the disk, tell it "guided - use entire hard drive", or whatever is closest to that (I don't remember the exact verbiage). The rest of the instructions should be self-explanatory. On a side note, if it seems like the computer is running *really* slow when you boot from CD, that is normal, as reading data of the CD is **very** slow compared to reading it off a hard drive.

One last thing - if all of this seems a little too intimidating, linux may not be for you, or it may not be for you right now. I suggest you head over to the Linux Documentation Project and read their Intro to Linux guide. That'll give you a good start in understanding linux fundamentals. **_[http://tldp.org/LDP/intro-linux/html/](http://tldp.org/LDP/intro-linux/html/)_**

And for the record, I'm a geek, not a nerd. _**[http://www.thinkgeek.com/tshirts/generic/6111/](http://www.thinkgeek.com/tshirts/generic/6111/)**_

---

### Post by jj-johjoh on 2008-05-14
Well, if you just said you don't like the new ubuntu (8.sumthing) you can download ubuntu 7.04, which is pretty stabble!
Just follow the steps from the previous post, but dowload [THIS]("http://au.releases.ubuntu.com/7.04/ubuntu-7.04-desktop-i386.iso") .ISO file instead.

The rest is pretty much the same as he's said.

If you need any more help just post here again, we'll be glad to do so.

P.S.: i love cheese!

---

### Post by Afkpuz on 2008-05-14
Sorry to hear that hardy isn't working for you.  Rest assured that my version is running better than my gutsy was, especially since I have an ati card and don't need to install xgl.  that makes me happy. any way, to revert back to gutsy, backup all your stuff.  Maybe get/borrow and external harddrive for this.  You could also burn your data to disc.  then, download an ISO of gutsy from the net.  Goto this page to view download servers and select the closest one to you, then choose 7.10, which is the version number for gutsy.  Make sure to pick your right cpu type and bit.  (i.e. AMD 64 bit, etc.)  Then, burn the iso to a disc and boot from it.  Installation is generally self-explanatory.  If you need any more specifics, let me know.

---

