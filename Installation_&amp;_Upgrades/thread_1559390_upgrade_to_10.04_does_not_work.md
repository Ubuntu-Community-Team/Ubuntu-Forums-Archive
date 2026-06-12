---
title: "upgrade to 10.04 does not work"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by stef-l on 2010-08-23
Have used 8.04 successfully for a couple of years, first as dual boot with XP then standalone.

Tried several times to upgrade to 10.04.  Used upgrade, used live CD.  Whichever method I've used, I get the first boot up that completes the install, but after that 10.04 will neither shut down (have to power off) and it will not then boot up again.  Everytime I have ended up having to reinstall 8.04, which works perfectly.

Last time I was on the forum someone suggested waiting till 10.04.1, which I duly did, and exactly the same happened.

This is getting me down.

I have a suspicion that there's a bug in the BIOS (that flashed up on a screen as I tried to reinstall) and I've come across references to grub, and to MBR on various posts.

Although I don't think I'm an idiot, I'd appreciate some simple, straightforward things I could try in an effort to sort things out.  I have the feeling that something fairly basic is wrong because I got out the XP disc in desperation one time, and even that wouldn't boot up and install.

ubuntu 8.04 linux 2.6.24-27 generic gnome 2.22.3
1GB memory, AMD Ahtlon XP2600+, 132.1GB hard drive
nvidia 6200 graphics card.

Thanks for any suggestions

---

### Post by mörgæs on 2010-08-24
Does it work with 9.10?

[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

---

### Post by stef-l on 2010-08-25
No luck here.

I have a 9.10 and an 8.10 CD, but neither will boot.  Just get 'searching for boot record from CD/DVD-0' then 'not found' and 8.04 boot up.

I think I'm either stuck with a corrupt MBR? or BIOS? or a GRUB issue?  Although I don't fully understand about any of these, I am willing to work through a set of instructions if I can understand them.  I have used terminal commands before.

There's no problem with installing the 8.04 CD.  The 10.04 CD sometimes behaves, but then after the installation I get the problem I described: no shutdown, no boot.  This has also happened when I upgraded online.

Thanks

---

### Post by mörgæs on 2010-08-25
Do the 8.10 and 9.10 disks work on other machines? 

If the machine boots from USB (not all do - it might be necessary to change BIOS settings), can you boot some of the versions? 

What happens if you run the memtest from 8.04? It might take all night.

---

### Post by stef-l on 2010-08-25
Have tested CDs for 8.10, 9.10 & 10.04 by putting them into  a laptop running windows XP.  All 3 run straight away and offer me the usual options for live session, install etc.  Haven't gone any further because it's not my laptop and so I shouldn't install another OS.

Have copied all the files fro 9.10 CD to a USB stick (hope this will be bootable, but couldn't find any other way to do it) and will try this on my computer after memtest finishes.

How do I know when memtest has done? it seems to be repeating itself - running for 2 and a half hours so far & 2 passes recorded?  will it eventually finish or do I stop it?

Thanks

---

### Post by stef-l on 2010-08-26
Update: I let memtest run overnight; test ran 14 times & no errors were reported.

Tried to install 9.10 from USB stick; got the message 'boot record found' but was then told to remove the disk & 8.04 booted up.  But I'm not sure I made the USB stick correctly.

Await your next suggestions

Many thanks

---

### Post by mebomechanicno1 on 2010-08-26
I have 9.10 running on a Vaio PCG X18 and had a similar problem with 10.04 to that described above, except that if I then run repair on 9.10 it tries to reinstall 10.04. I will sit on the sidelines and await developments, but will be happy to try to answer any questions about my version of this problem that may help.

---

### Post by mörgæs on 2010-08-26
There is no need for waiting. It is all about experimenting.

Good, we know that the memory is all right. Bad memory blocks can give a lot of strange and unsystematic errors.

If you are not certain that the 9.10 USB stick works: Does it boot on another machine? Keep in mind that old BIOS's sometimes don't want to boot a USB drive.

This might also be an idea:
[http://ubuntuforums.org/showpost.php?p=9758078&postcount=8](http://ubuntuforums.org/showpost.php?p=9758078&postcount=8)

Have you thought of upgrading the BIOS?

---

### Post by stef-l on 2010-08-26
So I downloaded a new bootable USB version of 9.10 and tried it; computer found boot record on the USB then:

"No default or UI configuration directive found! boot:"

And I did not know what command to give, so had to power off & here I am with 8.04 as ever.

I had thought about whether I should try & update the BIOS, but all the information I found when I searched for how to do it was via Windows, which I don't have.  And it sounded a bit risky...

---

### Post by stef-l on 2010-08-26
Another update...

Successfully downloaded 9.10onto a USB stick and installed it!  But... got to the very last stage where the button says 'restart now' and it wouldn't shut down - just got the yellow screen hanging.  Had to power off.

It boots up fine but will not shutdown or restart - have tried this several times, and clearly can't keep on powering off th computer all the time...

Now this is exactly what happens when I have successfully installed 10.04 in the past - it will not shut down.  Also, 10.04 is prone not to want to boot up either.

So I will now be reinstalling 8.04 again... (temporarily, I hope).

Do you think it would make a difference setting up the dual boot with 8.04 and 9.10?

Thanks

---

### Post by mörgæs on 2010-08-26
One of my machines does not want to shut down eigther. It shuts down almost to the end, but at the final stage it hangs, and I have to do it by hand. I don't think that it damages the system - I have not seen any indication on that, at least.

You could also try **sudo shutdown now**.

Else I don't have more ideas other than stay with 8.04. When support runs out in april 2011 you will have 10.10 and 11.04 to choose from.

---

