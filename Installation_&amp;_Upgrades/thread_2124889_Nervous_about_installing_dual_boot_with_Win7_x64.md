---
title: "Nervous about installing dual boot with Win7 x64"
date: 2013-03-12
forum: Installation &amp; Upgrades
---

### Post by cbiweb on 2013-03-12
Absolutely new to Ubuntu, a refugee from the Microsoft world.   Windows 8 made my decision for me.

I'm currently running Windows 7 Home Premium 64-bit on a Dell Inspiron 1750
I have downloaded and created the install disc for Ubuntu 12.10, and taken it for a test drive from the DVD.

Love it!

Now...  I want to install it side-by-side with my Win7 installation, but various tutorials on the Web have made me a little nervous due to so many different things that could go wrong, and so many things to check and keep track of; and a lot of standby fixes for all the what-ifs.  :shock:

My brother told me that he installed Ubuntu with Win7 with no problems, and all he did was follow the prompts, and never had to worry about all the contingencies.  But I'm not so brave as I have a lot to lose - even though everything is backed up - I can't spend a lot of time reinstalling everything if it all goes south. I do Web design and online marketing, so there are a LOT of programs and apps to reinstall, which takes a few days.  I've just finished recovering from a HD death, and I need to get productive again ASAP.

So my question is, what's the most reliable and least time consuming way to accomplish my goal here?  The information I find just makes my eyes glaze over because there are too many scenarios.  I realize that all angles have to be covered, but is it really such a touchy thing to install Ubuntu side by side with Windows?  Or is information overload making me too paranoid? lol

---

### Post by oldfred on 2013-03-12
No, but Microsoft & vendors have made it a bit more difficult as they have used all 4 primary MBR(msdos) partitions with Windows 7 installs.

Use Windows 7's disk tools to shrink the Windows 7 main partition and reboot a couple of times to make sure it has run its repairs and chkdsk.

But you will have to delete one partition if all 4 are used. Do not create partitions in Windows or it will convert to dynamic which does not work with Linux and even may create issues in Windows.
Often all vendors have a vendor utility like HP's disk utility. It is small and eaily backed up. Then you can delete it to make one larger extended partition in the free space. If you just want the default of / (root) and swap, you do not have to create any partitions manually, just let the installer install to the unallocated space. Do not use to overwrite entire drive option as that will erase all of Windows.

Some examples with screeenshots so you can see what will happen.
 Install options, Do not use erase entire drive unless that is really what you want.
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

      
 Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by zvacet on 2013-03-12
Installation is easy and simple.Maybe you want to look [this]("http://www.youtube.com/watch?v=PvP_4J2MUEc") or some similar video and after that install Ubuntu.You can dedicated more space for Ubuntu and make separate home partition but that is optional.

---

### Post by cbiweb on 2013-03-12
Thanks, guys.  The video was especially helpful to see how relatively simple it is.  The in-depth info in the first reply is good reference material, though it gives me more :shock: feelings, lol.

I'll go with the video and post back with the results. :)

---

