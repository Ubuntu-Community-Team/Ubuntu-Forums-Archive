---
title: "Slight Problem With Network Installation"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by s3a on 2007-08-21
Ok I found this page ([https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)) and unfortunately, it needs a high speed internet connection! 

I have two questions:
1)Is there a way to download the Breezy Badger CD off another computer and then do this without needing internet?
2) Can I do this whole process with Edgy Eft (6.10)? If I did, what would I need to do differently?

Please help me! I really need to get my laptop running flawlessly before school starts!

Thanks in advance!

P.S.
Can someone confirm if Airlink 101's USB AWLL3026 adapter works OUT OF THE BOX on Feisty Fawn? If it does, then change Edgy Eft in question #2 to Feisty Fawn.

---

### Post by tyggna1 on 2007-08-21
Hope [this]("http://www.aircrack-ng.org/doku.php?id=compatibility_drivers&DokuWiki=91dea4b75666129e4ad59840435ecab9") helps confirm compatibility.  Looks like that card isn't designed to be compatible with windows--and is based off a linux driver.  It might not work right out of the box--unless it's based off prism2 drivers in feisty.  

After a bit of diggin, it looks like that card is based off the Zydas chipset.  The ubuntu documentation says that the driver is installed on breezy and dapper, and you can read the installation instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211#head-0c0482fc5486ad8ed727830545b444fe5f9ea44c")
if it doesn't work right out of the box.

As for feisty (which is what I use, and my first linux) I don't think that zydas is pre-installed.  The module name for that is zd1211 -- but I couldn't find it using the terminal command
```
sudo modprobe -i zd1211
``` on mine...I might just be missing the right command name or file name though, and someone else would probably know.  As for the DHCP stuff, I don't know.

---

### Post by s3a on 2007-08-21
I also have the D-Link DWL-G122, but, that's the least of my concerns, what I really need is to know how to get this process to work without high speed internet!

---

### Post by logos34 on 2007-08-21
actually it's zd1211**rw** -- it's been rewritten for Feisty so your zydas-based awll3026 airlink *should* work just fine.  I qualify that because although it worked out of the box for me in Feisty, I was having problems getting it to work on a separate 6.10 edgy installation, and after googling around I learned that there are apparenty two chipset revisions that come with that adaptor, one of which will not work.  I guess I was lucky because mine had the right one, and I was able to get it to work in Edgy using a community-designed driver I downloaded.

Isn't there anyway you could download the iso at the public library, say, save it to a 1GB usb stick and then burn it to CD on a friends machine?

---

### Post by s3a on 2007-08-22
> **logos34 said:**
> actually it's zd1211**rw** -- it's been rewritten for Feisty so your zydas-based awll3026 airlink *should* work just fine.  I qualify that because although it worked out of the box for me in Feisty, I was having problems getting it to work on a separate 6.10 edgy installation, and after googling around I learned that there are apparenty two chipset revisions that come with that adaptor, one of which will not work.  I guess I was lucky because mine had the right one, and I was able to get it to work in Edgy using a community-designed driver I downloaded.

Isn't there anyway you could download the iso at the public library, say, save it to a 1GB usb stick and then burn it to CD on a friends machine?
I have the Ubuntu 6.06 LTS CD and 7.04 of Ubuntu and Kubuntu shipped to me! My uncle downloaded 6.10 and gave me the CD as well. So...I have the OS, so what do I do next?

Thanks in advance!

P.S.
I need to do this because my laptop's optical drive is broken.

---

### Post by s3a on 2007-08-22
Is it true that I can take the ~700 MB Ubuntu installation and split it through a load of floppies?

LOL, I would need 487-500 floppies! If there is a way to do split the ISO amongst 487 floppies, please guide me through the process as I am desperate to get my laptop to work!

Thanks in advance!

---

### Post by logos34 on 2007-08-22
> **s3a said:**
> LOL, I would need 487-500 floppies! If there is a way to do split the ISO amongst 487 floppies, please guide me through the process as I am desperate to get my laptop to work!

hahaha...stop, you're killing me!

---

### Post by s3a on 2007-08-22
Well....any help on installing through a network? I've posted this in so many different forms and no one seems to know anything! What am I going to do?! Please someone, help me!

*When I get this sorted out for me, I will definitely make a guide as it would be needed by people like me.*

---

### Post by s3a on 2007-08-22
If I had high speed, I wouldn't have this problem, so since I have a guide that would help me if I had it, all I need is help on getting the files to be taken from the hard drive of my desktop which in turn would be copied from a CD and not have it be downloaded from internet to hard drive and then be brought over to the laptop!

---

### Post by logos34 on 2007-08-22
If your cd drive doesn't work and you don't have broadband internet, this is about your only option (haven't tried it yet):
[URL="https://help.ubuntu.com/community/Installation/LocalNet?highlight=%28net%29"]
'Basic: Hands-On Interactive Network Server Edition Install'[/URL]

Or if you possibly get your hands on a USB stick AND this laptop Bios can boot from USB devices, there's this:
[https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=%28usb%29](https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=%28usb%29)
(-->contains link to Feisty version)

good luck

---

### Post by logos34 on 2007-08-22
another idea (but you've probably thought of this already):

--take the hard disk out of the lappy and put it in a 2.5" usb caddy, plug it into desktop pc, install Edgy 6.10 on it, then reinstall drive to laptop and hope it works.  You could buy an enclosure and then return after you get done.

---

### Post by s3a on 2007-08-22
> **logos34 said:**
> If your cd drive doesn't work and you don't have broadband internet, this is about your only option (haven't tried it yet):
[URL="https://help.ubuntu.com/community/Installation/LocalNet?highlight=%28net%29"]
'Basic: Hands-On Interactive Network Server Edition Install'[/URL]

Or if you possibly get your hands on a USB stick AND this laptop Bios can boot from USB devices, there's this:
[https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=%28usb%29](https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=%28usb%29)
(-->contains link to Feisty version)

good luck
I can't boot from USB but the first link seems to be just what I need!

"Ensure that you have a dhcp server (or a bootp server), a tftp (eg tftp-hpa) server, and an nfs server available on your network. If not, install them onto a machine (or over a set of machines if you want to complicate things)."

How do I install what is required on my machine? I mean like, are those the names of the programs or I have to find programs that do what is said in the quotation? And does this mean I need to run Ubuntu Linux on my desktop in order to do this? Does it have to be server edition or can it be the desktop one?

I'll continue this tomorow, hopefully I will see success, but now I am too tired to continue and will sleep...

---

### Post by s3a on 2007-08-22
> **logos34 said:**
> another idea (but you've probably thought of this already):

--take the hard disk out of the lappy and put it in a 2.5" usb caddy, plug it into desktop pc, install Edgy 6.10 on it, then reinstall drive to laptop and hope it works.  You could buy an enclosure and then return after you get done.

That is very smart!!!! I can't believe I didn't think of that! Probly because I'm use to Windows XP not functioning if you install it through another computer! Well, I'll still try network thing so please help with the installation of the required programs, and ill check prices on the cases!

Thanks!

P.S.
Now, I am going to sleep for real!

---

### Post by logos34 on 2007-08-22
on second reading it looks like you'd need the Server install edition CD (~492MB), then you'd need to download the additional pkgs listed (dhcp3, etc).  So I guess that's out.

---

### Post by logos34 on 2007-08-22
> That is very smart!!!! I can't believe I didn't think of that! Probly because I'm use to Windows XP not functioning if you install it through another computer! 

that's why i said 'hope' it works--ubuntu is more flexible than windows but that doesn't mean you won't have any problems.  (especially if the two computers are different platforms, ie amd and intel)

---

### Post by s3a on 2007-08-22
> **logos34 said:**
> that's why i said 'hope' it works--ubuntu is more flexible than windows but that doesn't mean you won't have any problems.  (especially if the two computers are different platforms, ie amd and intel)
They are both intel processors except desktop is pentium 4 while laptop is pentium 3. I have a pentium 3 desktop computer as well in another room. So, I'll just take the hard drive of the other desktop computer (pentium 3 pc), bring it over to this computer and install Ubuntu then bring it back there. That should be a good simulation, right?

P.S.
Shouldn't the Ubuntu installation adjust to the platform switch as would a Windows 98 installation?

---

### Post by logos34 on 2007-08-22
> **s3a said:**
> They are both intel processors except desktop is pentium 4 while laptop is pentium 3. I have a pentium 3 desktop computer as well in another room. So, I'll just take the hard drive of the other desktop computer (pentium 3 pc), bring it over to this computer and install Ubuntu then bring it back there. That should be a good simulation, right?

I would think so.

No experience with win98, but as I said ubuntu is rather adaptable.  I come across a lot of posts from people who plugged their ubuntu hard disks into completely different/new machines and it booted right up with nary a complaint.  Others have problems.

---

### Post by s3a on 2007-08-22
> **logos34 said:**
> I would think so.

No experience with win98, but as I said ubuntu is rather adaptable.  I come across a lot of posts from people who plugged their ubuntu hard disks into completely different/new machines and it booted right up with nary a complaint.  Others have problems.
So, would it be safe to say that in the majority of cases, it has worked successfully?

---

### Post by Left hand of Gaia on 2007-08-22
On the topic of swapping drives to install:

I just dropped a hd from my old amd system into my new xeon system, other then driver issues (video card mainly) it picked up and ran with it.  You should be fine installing it, though you should double check you drivers/laptop specific packages when you get it re-installed.

Regards,

---

### Post by s3a on 2007-08-23
> **Left hand of Gaia said:**
> On the topic of swapping drives to install:

I just dropped a hd from my old amd system into my new xeon system, other then driver issues (video card mainly) it picked up and ran with it.  You should be fine installing it, though you should double check you drivers/laptop specific packages when you get it re-installed.

Regards,
Thanks! Now, I've got a solution to my problem! I will post back when I have done it.

---

