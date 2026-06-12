---
title: "Installed ubuntu 11.04 but going back to 10.10"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by yosepht on 2011-04-29
Whether it is just made unconfigurable or difficult to configure I don't
like it. Can't move the panel from top to bottom, Firefox did not have 
pull down menus for bookmarks etc. Where the did the Application ,Places
and System panel menus go? In 10.10 and before I could right click on the
desk top and add to the panel but, 11.04 does not even respond to right
click.
 If this is a bug that has a fix please help but if this is normal for 11.04
please let me know how I can make 10.10 the default partition to boot.

thanks for taking the time.
 Yo.

---

### Post by kansasnoob on 2011-04-29
I made some notes in posts #1 And #2 here:

[http://ubuntuforums.org/showthread.php?t=1718631](http://ubuntuforums.org/showthread.php?t=1718631)

You can make 11.04 look just like 10.10 :D

---

### Post by CrazyJesse on 2011-04-30
I don't like how the left-sided quicklaunch/taskbar combo doesn't fully pop-out every-time. There's other sluggishness menu issues. I liked how the old top taskbar stayed when firefox was open. Applications,Places,and System up at the top is missing(which changes EVERYTHING). Everything is shuffled around. Can't find a thing anymore.I'm a bit lazy to actually want to scope out and find things ,but not TOO lazy to use Terminal,which is where now? They changed TOO MUCH, too soon. Rest in peace ya Natty whatever.

---

### Post by CrazyJesse on 2011-04-30
Oh look up there!! Hmmmm.

---

### Post by yosepht on 2011-05-01
Thank you very much that was very helpful. I went back to classic. May be 
some day I will understand the appeal behind Unity desktop and go back to it.

---

### Post by PalugDitzi on 2011-05-05
Even after reconfiguring the desktop to achieve the pre-11.04 look and feel I am finding the following issues:

+Instabilities in browser Firefox
+Nautilus permissions issues not previously present
+Unstable desktop panels

Unfortunately I don't have the time these days to hunt down and debug all the issues nor the patience.  Just want something as efficient as recent prior releases were.

I've been using Ubuntu since early Warty, and a Linux user since '94.
Currently planning on going back to 10.10 or 10.04.

Wish there were an automated downgrade option or utility for the same in a a release.

---

### Post by maddagger on 2011-05-13
I agree! I am a Ubuntu convert after years of having to put up with Windows taking more and more control away from the user. And now 11.04 has done just the same as WIN!
So frustrated with new look, but even though the classic look, looks the same, it is causing my computer to hang all the time, and the disappearing menus is driving me nuts! I left Win to get away from crashing programs! I will be reinstalling 10.10 next week, and switching to a different distro if this nonsense continues.

---

### Post by elianto on 2011-05-13
I want to add my self to express the frustration. I'm a linux user since 96 ubuntu user since 8.04 and looks like things are going backward from version to new ones, especially about testing new version before going public. 
I'm trying  now to upgrade from 10.10 but after the do-release-upgrade stopped because of a dpkg error I fixed manually altering /var/lib/dpkg/status and /var/lib/dpkg/available for a bug similar to [this ]("https://bugs.launchpad.net/ubuntu/natty/+source/dpkg/+bug/773022"). Now the pc boots at the gdm/kdm (I tried both) and the keyboard and mouse are locked. Any suggestion?
follows a little RANT
The reason I wanted to give 11.04 a try was because since a while the kde desktop took 20 min to startup at **every start up** because of several nepomuk service trying to index who knows what. (I've even tried to restart from a fresh .kde, moving out data but nothing, kde was still taking long time to start, freezing completely the pc in the meanwhile. I had to switch to gnome for getting my work done... I mean... don't want to troll at the opposite but this is **not normal** it's very winlike 
Trying to be less provocative I know things are not easy, and I think we all have to realize that probably this is the effect of the huge hardware and software "biodiversity" out there and with numbers comes complexity in software stacks. Nevertheless I think, as a user perspective, there is a lack of software testing and lack of consideration on how much minor problems can affect a large userbase and the overall impression of opensource/freesoftware as real alternative in a production enviroment.
regards

---

### Post by elianto on 2011-05-13
I want to add my self to express the frustration. I'm a linux user since 96 ubuntu user since 8.04 and looks like things are going backward from version to new ones, especially about testing new version before going public. 
I'm trying  now to upgrade from 10.10 but after the do-release-upgrade stopped because of a dpkg error I fixed manually altering /var/lib/dpkg/status and /var/lib/dpkg/available for a bug similar to [this ]("https://bugs.launchpad.net/ubuntu/natty/+source/dpkg/+bug/773022"). Now the pc boots at the gdm/kdm (I tried both) and the keyboard and mouse are locked. Any suggestion?
follows a little RANT
The reason I wanted to give 11.04 a try was because since a while the kde desktop took 20 min to startup at **every start up** because of several nepomuk service trying to index who knows what. (I've even tried to restart from a fresh .kde, moving out data but nothing, kde was still taking long time to start, freezing completely the pc in the meanwhile. I had to switch to gnome for getting my work done... I mean... don't want to troll at the opposite but this is **not normal** it's very winlike 
Trying to be less provocative I know things are not easy, and I think we all have to realize that probably this is the effect of the huge hardware and software "biodiversity" out there and with numbers comes complexity in software stacks. Nevertheless I think, as a user perspective, there is a lack of software testing and lack of consideration on how much minor problems can affect a large userbase and the overall impression of opensource/freesoftware as real alternative in a production enviroment.
regards

---

### Post by manor.parmar on 2011-05-14
i had ubuntu 10.10...the today i tried to upgrade it to 11.04 but some error occured and now ubuntu 10.10 is not working and  also it does not allow ubuntu 11.04 to get install on windows 7....error like this occurs:- 
" cannot download the metalink and therefore the iso. for more infomation please see the log file: c:\users\hp\appdata\local\temp\wubi-11.04-rev211.log"

i am unable to understand what to do...i tried to uninstall 10.10 but still the same error occurs....please any body help me with this.....my id is [email]manor.parmar@yahoo.com...please[/email] reply on this....

---

### Post by elianto on 2011-05-15
I solved most of my problem, akonadi was going crazy I had to wipe out .kde .config and this happened several time (about each new distro) I think at least is not normal, btw 11.04 overall seams to work better in kde

---

### Post by elianto on 2011-05-15
> **manor.parmar said:**
> reply on this....
I advice you to make an usb key with the livecd of kubuntu daily build [download it here]("http://cdimage.ubuntu.com/kubuntu/daily-live/current/")
to transfer the downloaded image to usb use the Universal Installer [download it here]("http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe")
and run it ([instruction here]("http://www.ubuntu.com/download/ubuntu/download"))
... this is the best way to try it and install it , don't wubi

---

### Post by daleim on 2011-05-27
I am running Ubuntu on my computer which is about 7 years old. So a bit long in the tooth I know. I ran 10.04 really well and most of 10.10. But started to get strange with the last lot of updates. I've upgraded to 11.04 and it wont run unity, no problem that's fine but with the latest update it not longer boots to a desktop I just get a white page with what looks like ascii. I can get it to boot by using the previous page mode. So I guess it will no be save as much data as possible and go back to 10.10 or 10.04.
 
Not wrapped in Unity as it seems to be just another layer of stuff making it harded to find what I already knew how to work. Been using Ubuntu since 9.04 and like it cause it boots fast.

---

### Post by crienoloog on 2011-05-27
Add me to the list of frustrated persons.
Even in Classic Look screen is erratic and computer crashes, window headers disappear.
I need a downgrade button to return to 10.10 !!!!

Hope the developers get notice of these posts...

Maybe this is an idea: [http://www.omgubuntu.co.uk/2011/05/pre-unity-ubuntu-netbook-launcher-is-resurrected-put-in-a-ppa/](http://www.omgubuntu.co.uk/2011/05/pre-unity-ubuntu-netbook-launcher-is-resurrected-put-in-a-ppa/)

---

### Post by cybermanic on 2012-02-23
I also does not like new desktop and organisation. This is kinda MSWindows-like. And upgrading from 10.10 to 11.04 I've lost wireless connection. Must downgrade.

---

