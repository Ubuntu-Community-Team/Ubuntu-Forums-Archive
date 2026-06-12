---
title: "Installation errors"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by catastrophee on 2005-04-13
Im having a hard time installing ubunto as it froze when it was installing the base system at 6%. 

Also when i was setting it up i accidently erased my whole C drive in the partition thing to install this linux.

Im a linux noob and ive tried the live version from CD and it worked but the permanent one doesnt work.... 

I can use linux with windows xp right ? I currently have a 40gb hd and a 120gb.

---

### Post by Dr Gonzo on 2005-04-13
Well, sorry you nuked C:, but you have to be really careful when partitioning.  Always go slowly and methodically through your installations.  Don't rush.

So, what sort of partitioning scheme do you have?  Do you have an entire drive you can devote to Ubuntu?  If so, just make sure it's the correct one, not the one with XP on it.  The installer should detect other OSes when it runs the Grub (GRand Unified Bootloader) installation.  If not, it's pretty easy to add it yourself.

As for the freeze -- Have you attempted the installation more than once?  If not, try it again, it might work on its own.  If not, I'd first try using a different filesystem for your root drive.  Use the regular partitioner, let it fail, then restart the installer.  Then, use expert partitioning, and have it use whatever partitions it created initially, but use a different filesystem.  ReiserFS is a good one, as is JFS.  ext3 is the default, I think, and it's actually one of the slower journalled (=easier recovery if you get a power outage) filesystems.

Hope this helps a little.

---

### Post by catastrophee on 2005-04-13
Im not sure what kind of partitioning scheme i have .... i got my 120g hard drive and i dont want that one touched by anything. I was told I can use win xp with ubuntu ....

---

### Post by Dr Gonzo on 2005-04-13
Okay, yes you can.  That's true.  You can calm down about that one.  :wink: 

The installer should recognize both hard drives, as far as I know.  One drive, the drive on your first IDE bus, will be called /dev/hda, and the second one will be called /dev/hdb.  You may need to do manual partitioning.  If you do, you should be able to look at the help option that the installer gives you once you're in the manual partitioner.

If you want to know the best way to use your space, you should create a swap partition that's twice the size of the memory on your machine.  So, for a 512MB machine, you'd have a 1024MB swap partition.  Then, you can either use the rest of the hard drive for your root partition, or you can have part for / and part for /home.  I do the latter, as it allows me to keep all of my data if I ever need to reinstall.

Also, in the future, you should try to be as explicit as possible when you're posing a problem.  The more information you can give, the better.  Tell exactly the steps you went through, and it's much easier to figure out what went wrong.

---

### Post by catastrophee on 2005-04-13
[QUOTE=Dr Gonzo]Okay, yes you can.  That's true.  You can calm down about that one.  :wink: 

The installer should recognize both hard drives, as far as I know.  One drive, the drive on your first IDE bus, will be called /dev/hda, and the second one will be called /dev/hdb.  You may need to do manual partitioning.  If you do, you should be able to look at the help option that the installer gives you once you're in the manual partitioner.

If you want to know the best way to use your space, you should create a swap partition that's twice the size of the memory on your machine.  So, for a 512MB machine, you'd have a 1024MB swap partition.  Then, you can either use the rest of the hard drive for your root partition, or you can have part for / and part for /home.  I do the latter, as it allows me to keep all of my data if I ever need to reinstall.

Also, in the future, you should try to be as explicit as possible when you're posing a problem.  The more information you can give, the better.  Tell exactly the steps you went through, and it's much easier to figure out what went wrong.[/QUOTE]
 A swap partion eh ? i had that configured it was like a 1.7gig but it just didnt work man i dont remember the error. But anyway the darn ubunto thing froze at 6% finding a single file i forgot the namei think it was "ubtutils" or something similar to that!

I guess ill see if i can install it once more and post my errors ...... i just need to get through the installation! But i wont TOtally delete a hard drive like it asks me to ..... 


At the moment im also battling a problem with my AGP 3.0 drivers for my VIA KT4V msi 6712 motherboard. Blah im blabbering.....

---

### Post by catastrophee on 2005-04-13
[QUOTE=catastrophee]A swap partion eh ? i had that configured it was like a 1.7gig but it just didnt work man i dont remember the error. But anyway the darn ubunto thing froze at 6% finding a single file i forgot the namei think it was "ubtutils" or something similar to that!

I guess ill see if i can install it once more and post my errors ...... i just need to get through the installation! But i wont TOtally delete a hard drive like it asks me to ..... 


At the moment im also battling a problem with my AGP 3.0 drivers for my VIA KT4V msi 6712 motherboard. Blah im blabbering.....[/QUOTE]
 Ok anyway I wiped out my C drive again and the installation failed at 6% like expected.

Im running right now off of the ubunto live cd.... its pretty lame considering i dont have my hard drives functioning. So i need to reinstall windows on the 40gig hard drive, since i cnat install the ubunto... 

i consdering instlaling different version of linux bcuz this aint working to well :)

---

### Post by Dr Gonzo on 2005-04-13
I fail to understand how you nuked C: again.

Why did you attempt to install to the 120 GB drive again?  If one is /dev/hda, and you just tried to install to /dev/hdb, try the other one.  *Use the manual partitioner, and read the help that comes with it!*

Give up now, and you'll just kick yourself.  You can do it.

---

### Post by catastrophee on 2005-04-13
I dunno what your talking about /dev/hdb i dont see that anywhere in my installation.

I attempted to write a partition on the 40g hard drive then i made another one on it .. then it was installing and it froze!

---

### Post by Dr Gonzo on 2005-04-13
Was C: on the 40 GB drive initially?

Did you try installing onto a different filesystem type?

Maybe you have a corrupt cd.  Try burning a new one.

---

### Post by catastrophee on 2005-04-13
[QUOTE=catastrophee]I dunno what your talking about /dev/hdb i dont see that anywhere in my installation.

I attempted to write a partition on the 40g hard drive then i made another one on it .. then it was installing and it froze![/QUOTE]
 its not like i want to give up but its just so hard ... perhaps my CD is corrupted ? since it freezes finding a file on the CD ... I assume it is right ? Oh and the exact file is "Bsdutils" thats when it freezes

---

### Post by Dr Gonzo on 2005-04-13
Yeah, I'd try burning a new one.  If you get to the partitioner, keep hitting <go back>, which will take you to a menu.  From there, there's an option to check the cd.  You could try that.

Also, what I was talking about is if you get to the manual partitioner, it should list every partition on every disk.  So, it'll say something like "IDE1 Master (hda)" and "IDE1 Slave (hdb)" or some such stuff.  Make sure you're installing to the correct disk.

What keeps confusing me is that you somehow keep wiping out your Windows partition.  Is it on the 40 GB drive?  Where is C: that you keep nuking?

Remember that those are *Windows* drive designations.

Here's a quick primer on Unix drive designations:

for IDE drives...
1st IDE bus, Master is /dev/hda
1st IDE bus, Slave is /dev/hdb
2nd IDE bus, Master is /dev/hdc
2nd IDE bus, Slave is /dev/hdd

Grub names these differently.  If your first drive is /dev/hdb (meaning there *is no master* on that bus) then /dev/hdb is (hd0) in Grub.  However, most of the time, your first drive is /dev/hda, so in Grub it'd be (hd0).  Note that it starts with 0 in grub, but not in Linux.  So, /dev/hda1 (1st IDE bus, master, first primary partition) would be (hd0,0) in Grub.

---

### Post by catastrophee on 2005-04-14
When checkin integrity i froze at 20%......... its definitly a cd error right ?

Imwiping out C drive by selecting IDE 1 or whatever the 40gig HD is labeled as and formatting it to install ubuntu linux. Right now i just wrote a 10g partition to that HD win xp which im on now and have about 28g of unpartitioned space on the C drive. 

It was all done intentional and i was aware that i was wiping them out.

---

### Post by ate50eggs on 2005-04-14
I don't know if this will help. I had two hanging errors during the install. One at about 6% and one at abour 75% (right after it promted me about the kernel)

I tossed the CD and burned a new one. That got me past the first error.

The second one went away when I changed my journaling from ReistFS to Ext3.

Not really sure what was behind these problems or why those solutions worked.

---

