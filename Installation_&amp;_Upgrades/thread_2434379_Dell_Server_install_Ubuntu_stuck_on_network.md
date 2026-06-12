---
title: "Dell Server install Ubuntu stuck on network"
date: 2020-01-04
forum: Installation &amp; Upgrades
---

### Post by cj8281 on 2020-01-04
I recently purchased a Dell PowerEdge T110 II.  CPU i3 3.3ghz, 16gb ecc Udimms, on board video and lan.  I put a 32gb usb stick in one of the internal usb ports.  I was planning on using it for the OS.  I created a usb stick to install ubuntu-18.04.2-live-server-amd64.  The install works up to the step were I try and configure the network.  The page looks like this one: [https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-server#6](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-server#6)  I have tried changing settings but it never goes over 50% and then restarts that page again.  Not sure what I am doing wrong.  

I purchased the machine (actually 2 of them, the other has a Pentium something or other at 2.93ghz) from University surplus.  They didn't come with hard drives so I sourced some 3tb sas drives and a 32gb ssd.  Would it be better to use the ssd instead of the usb stick for the OS?  I think I can raid the 3 sas drives together and have them separate from the ssd if that would be the better way to go.  Or would it be better to not raid the sas drives and use them individually and possibly not even use the ssd??  
I want to make this into a file server for home use, a place to store a bunch of files in a central location instead of having a bunch of different files on a bunch of different machines.
I have played with SUSe 9.2 in the past but I really don't know much about Linux.
Any help would be greatly appreciated
Thank you in advance.

---

### Post by CelticWarrior on 2020-01-04
Just because it's server hardware doesn't mean you necessarily need to install the server version. For home use the regular desktop edition makes more sense and that one definitely doesn't require setting up the network during installation. I'm not familiar with the server edition so I'm not sure if that step can be ignored.

---

### Post by cj8281 on 2020-01-14
I went into the settings on the Dell, I changed the IPv4 settings to manual and entered an IP address, still the same.  I changed the settings to automatic DCHP, the same thing.  I disabled the network adapter in the bios and it still would not continue past that same page on the install.
Could it be a bad install program or something like that?

---

### Post by CelticWarrior on 2020-01-14
Again, no idea why you're insisting in the server version. Why don't you try the desktop version and troubleshoot from there?

Also take a look at [https://askubuntu.com/questions/1042364/install-18-04-server-without-network-connection](https://askubuntu.com/questions/1042364/install-18-04-server-without-network-connection)

---

### Post by cj8281 on 2020-01-14
Thank you for the link.  I will try what the others have posted.  Not sure why mine would not work with the network cable plugged in.  The rest of the computers on the network have no issue accessing the internet.  I will also try and download the regular desktop version and see if that will work.  The other issue that I am having is this server won't play nice on my KVM.  It won't show as active therefore it is not able to be switched to.

---

### Post by mörgæs on 2020-01-18
Servers often have a weak graphics card so installing a regular desktop can be a pain. 

A good start will be to list all hardware details. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by cj8281 on 2020-01-18
Update:  Not sure what changed but this morning when I started the server after going through the bios settings, when it reposted it actually had an ip address in the ipv4 settings instead of zeros.  I didn't change any settings, just looked through them to see if I could see anything that was off.  I also reformatted the usb stick and installed the full version of server and not the live version.  It looks like it installed fine.  Now the problem is the screen is too far to the left and I can't see what it says other than: uServer  ttyl  and then below it I can see the very edge of a blinking cursor.  I think uServer is the end of ubuntuServer which is the server's name.  Not very imaginative I know.

to [**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=939075") sorry it doesn't seem to do anything when I type that in.
It is a Dell Poweredge T110 II server, it has an i3 2120 processor, 16gb of ecc ddr3 ram, a single Seagate 500gb hard drive, all of the other devices are on the motherboard, there are no expansion cards installed. I do have a Radeon 3450 video card that I can install, it has 256 mb of ram, would that be better to install the desktop version of ubuntu?  The sata is set to ahci  and the bios is set uefi.  Does that help?

---

### Post by mörgæs on 2020-01-18
*If* you decide to run a desktop environment the 3450 is most likely better than the standard graphics processor. Still I recommend a lighter Buntu (like Xubuntu) over Ubuntu.

---

