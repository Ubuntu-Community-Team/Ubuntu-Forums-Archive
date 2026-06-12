---
title: "burn CD or  not to, that is the question"
date: 2009-06-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2009-06-11
Through other releases, I've burned and installed every Alpha. Is that needed or can I rely on the updates to upgrade through the final release?

---

### Post by LKjell on 2009-06-11
In theory you can update with the update manager. In practise sometimes you will encounter problems where you likely have to do a fresh install.

---

### Post by theozzlives on 2009-06-11
> **LKjell said:**
> In theory you can update with the update manager. In practise sometimes you will encounter problems where you likely have to do a fresh install.

I just want a way around wasting 8 CDs every release.

---

### Post by ronacc on 2009-06-11
if your box will boot from a usb stick , you can use that instead of a cd .updating will keep your software upto date since the cd's are just a snapshot of the repos at a point in time  but you could possibly missout on something like the change to grub2 unless you manualy installed it , also updating does not test things that only run during an install like ubiquity , so it is up to you which route you use .I usualy just update until I get my test box in such a state of disarry through hacks and workarounds that a fresh install is called for .

---

### Post by LKjell on 2009-06-11
Then the answer is to have patience and wait for the final release before you begin upgrading. If you are trigger happy with pressing the update button you might try Gentoo or Arch distribution.

---

### Post by ato on 2009-06-11
What about CDRW :D

---

### Post by theozzlives on 2009-06-11
> **ato said:**
> What about CDRW :D

I do have a CDRW, my test computer won't boot USB.

---

### Post by jimv on 2009-06-11
I would just keep upgrading until something breaks, which may or may not happen.

---

### Post by LKjell on 2009-06-11
To tell you a story I spend a day once to find a cdrw to burn Ubuntu on. Not easy to find a vendor that just sell you one cd nowadays. After I bought it I released that cd -r are actually very cheap. And they burn faster than rw plates.

---

### Post by ronacc on 2009-06-11
Yes where I live , Orlando,Florida,US , cd-r or +r run $15>17 for a 100 disk spindle and dvd's are about $22 for the same , cheap enough to use for party coasters or shims for a table leg :lolflag:

---

### Post by Ravernomina on 2009-06-11
IF you wana start booting from a USB. If you bought your computer from 2003 or below then you need a BIOS update that will usually let you boot from the USB. I did that and i can now boot from the external hard drive to Use Mac OS X :).

---

### Post by LKjell on 2009-06-11
Exactly. But then we have this environment problem so using cd-rw might be more beneficial in the long run. Or usb stick. However there are another way to save you the 8 cds. It is possible to make grub boot a local cd image and let you do a fresh install assuming you do not override the files when you do the install. You can do that by making partitions. The catch is I cannot remember how to do it. But you might do a "fedora upgrade network" search on the internet. Since there when you are going to upgrade you have to burn a dvd...

---

### Post by zenarcher on 2009-06-11
Personally, I use RW-CD's and merely erase and reuse them when a new test release comes along.

Cheers,
zenarcher

---

### Post by Ravernomina on 2009-06-11
I still just say Update your BIOS. Its scary at first when your gonna do it as long as you done your research your fine. Plus your compute runs better and my Mobo supports more RAM to :).

---

### Post by psyke83 on 2009-06-11
> **theozzlives said:**
> I just want a way around wasting 8 CDs every release.

Uhm, how about using a single rewritable CD or DVD? Yes, you can burn a CD image onto a DVD (and it usually has a faster read rate than CD-RWs).

---

### Post by andrewabc on 2009-06-11
cd-rw
Best solution. Use it. Buy a 10 pack, and you're set.

---

### Post by theozzlives on 2009-06-12
> **andrewabc said:**
> cd-rw
Best solution. Use it. Buy a 10 pack, and you're set.

I just burned Alpha 2 to my only RW. I know it won't last forever so I'll hafta get more soon.

---

### Post by Gina on 2009-06-12
With one of my older computers, whilst it didn't have "Boot from USB", I found it would accept a USB memory stick as a hard drive and was happy to boot from it.  Write a USB stick with Ubuntu, stick it in a USB port and see if your BIOS can change to boot from that "HD".  I only found this by playing about - I thought I couldn't use a USB stick to boot from.  Another, newer, machine does have "Boot from USB" option but won't boot from a USB stick that way - you have to use it as a hard drive.  Then it's fine.  Weird eh?! :lol:

---

### Post by Slug71 on 2009-06-12
> **jimv said:**
> I would just keep upgrading until something breaks, which may or may not happen.

This.

---

### Post by novafluxx on 2009-06-12
> **zenarcher said:**
> Personally, I use RW-CD's and merely erase and reuse them when a new test release comes along.

Cheers,
zenarcher

This is exactly what I do. A single CDRW. I know it will fail eventually, but these babies can go through hundreds of burns, and thats a lot of *buntu!

I usually start with a late alpha and then maybe burn the final to that CDRW and do a reinstall

---

### Post by PreviousN on 2009-06-12
You can sometimes **edit your grub menu.lst to boot to a usb**. This is supposedly even if your bios doesn't support it. I haven't done it but I hear it can be done. Check it out!
Google is your friend. I didn't read this page, and can't vouch, but it's the first result in google: 
[http://64.124.13.3/hacks/USB_Boot_using_GRUB.html](http://64.124.13.3/hacks/USB_Boot_using_GRUB.html)

And a result from ubuntu forums:
[http://ubuntuforums.org/showthread.php?t=992426](http://ubuntuforums.org/showthread.php?t=992426)

Also, what's in the new alpha? :-P 
On a side note, are you a developer or something? I can't think of a reason to install all those alphas, unless you're looking to see if hardware in your computer has become supported or fixed.

---

### Post by theozzlives on 2009-06-12
> **PreviousN said:**
> 
On a side note, are you a developer or something? I can't think of a reason to install all those alphas, unless you're looking to see if hardware in your computer has become supported or fixed.

I'm a technician, I like to stay on top of things before the consumer gets them. I'm also testing Windows 7 (used 2 DVDs and still not impressed).

---

### Post by Didius Falco on 2009-06-12
I'm betting that, as a tech, you've no shortage of hard drive storage space. An alternative to burning every alpha would be to set aside a large partition and use Partimage (or your favorite linux imager) to back up your installs every few days.

That way, if you run into an unrecoverable problem, you can simply restore it and wait for that problem to be resolved before updating again.

That's the method I'm using, with an updated image every 3-5 days, depending on how many updates I get, using a customized Ubuntu 9.04 Live Recovery CD.

Regards,

Didius

---

### Post by theozzlives on 2009-06-13
> **Didius Falco said:**
> I'm betting that, as a tech, you've no shortage of hard drive storage space. An alternative to burning every alpha would be to set aside a large partition and use Partimage (or your favorite linux imager) to back up your installs every few days.

That way, if you run into an unrecoverable problem, you can simply restore it and wait for that problem to be resolved before updating again.

That's the method I'm using, with an updated image every 3-5 days, depending on how many updates I get, using a customized Ubuntu 9.04 Live Recovery CD.

Regards,

Didius

The computer I'm testing on doesn't matter if an install gets hosed. I won't try a main computer until a Beta or RC at the earliest. To those who suggested the CD-RW, it didn't work... I tried both live and Alternate. Maybe a bad CD-RW. You're right about the space, but I make a tarball on my HDs.

---

### Post by PreviousN on 2009-06-13
Anyways, what I meant was that you can use unetbootin and a flash drive to install the every new alpha to a flash drive, instead of using a cd.

---

### Post by Asham on 2009-06-13
> **PreviousN said:**
> Anyways, what I meant was that you can use unetbootin and a flash drive to install the every new alpha to a flash drive, instead of using a cd.

This is what you normally do if you have a computer without cd/dvd drive, such as a netbook. It works very well and I think USB devices are faster than reading from disc.

---

### Post by robert.rankin.jr on 2009-06-13
What I do is use virtualbox with a virtual partition that links with my real partition. Can do fresh installs from ISO images without burning or writing to USB. Nice and simple.

VBoxManage internalcommands createrawvmdk -filename /home/robert/sda3.vdmk -rawdisk /dev/sda3 -register

Robert

---

### Post by theozzlives on 2009-06-14
> **robert.rankin.jr said:**
> What I do is use virtualbox with a virtual partition that links with my real partition. Can do fresh installs from ISO images without burning or writing to USB. Nice and simple.

VBoxManage internalcommands createrawvmdk -filename /home/robert/sda3.vdmk -rawdisk /dev/sda3 -register

Robert

HEY! I should've thought of that. I use VirtualBox for Windows 7, why not Ubuntu. Be one less machine to jack with.

---

### Post by andrewabc on 2009-06-14
> **Asham said:**
> This is what you normally do if you have a computer without cd/dvd drive, such as a netbook. It works very well and I think USB devices are faster than reading from disc.

Correct. Loading ubuntu from usb instead of cd is much faster.

According to my tests [here](http://ubuntuforums.org/showthread.php?t=1107298):
> 22 minutes to burn beta to cd-rw
3:48 to boot beta on cd-rw

2:05 to install beta to usb using 2gb kingston
1:27 to boot to beta desktop using 2gb kingston

1:15 to install beta to usb using 4gb oczrally2 1:14 second test.
1:20 to boot to beta desktop using 4gb oczrally2 
USB is ~2.85 faster than CD to boot to desktop.
For me it is almost as fast as my installed ubuntu. That is what makes testing with usb great. It is really fast with no lagging. I do install using cd though, because of fstab thinking usb is cd-rom if installing from usb.

---

### Post by theozzlives on 2009-06-15
Well, it works fine using the iso in VirtualBox. But I bought a new pack of CD-RWs cause I wanna see how it acts in a dual boot situation. The live CD didn't work (couldn't start GNOME display, I'm installing the alternate now.

---

### Post by theozzlives on 2009-06-16
> **theozzlives said:**
> Well, it works fine using the iso in VirtualBox. But I bought a new pack of CD-RWs cause I wanna see how it acts in a dual boot situation. The live CD didn't work (couldn't start GNOME display, I'm installing the alternate now.

I figured I was moving to a different subject so I made a new thread... [http://ubuntuforums.org/showthread.php?p=7465279#post7465279]("http://ubuntuforums.org/showthread.php?p=7465279#post7465279")

---

### Post by hugmenot on 2009-06-16
I see no reason to re-install from scratch each time. I have always been installing Debian or Ubuntu once afresh on each machine and then dist-upgraded through many releases. The APT system is very advanced and made to support exactly this process. It&#8217;s just a pain to recreate your installation every time. Why bother?

Sometimes during the devel period there might be minor hiccups. But after a while you figure out how to resolve these issues. Most often it just means to cancel the dist-upgrade and wait for a couple of days so that dependencies get sorted out.

BTW, there&#8217;s another option: [Netbooting a Live CD Image]("http://ubuntuforums.org/showthread.php?t=1112209&highlight=pxe+live")

---

