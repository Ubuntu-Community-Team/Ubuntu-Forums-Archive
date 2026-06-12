---
title: "TRIM support with OCZ Vertex 4 SSD in 11.10"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by manfromthezoo on 2012-04-23
Hello, campers.

I have a conundrum. Have bought the above SSD, put a clean install of 11.10 onto it, and can't seem to get TRIM support working.

I'm running the test [here]("http://sites.google.com/site/lightrush/random-1/checkiftrimonext4isenabledandworking"), which should return all zeroes, if TRIM has been enabled properly (yes, it's been setup properly in fstab).

This is what I'm getting instead:
[COLOR="Red"]
/dev/sda:
reading sector 804864: succeeded
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff
ffff ffff ffff ffff ffff ffff ffff ffff

If the sector isn't filled with 0s, something is wrong with your
configuration. Try googling for "TRIM SSD Linux".[/COLOR]

Any ideas? I'm going nuts trying to figure out what is wrong. All updates applied to 11.10, btw.

Thanks.

---

### Post by pqwoerituytrueiwoq on 2012-04-23
you can enable trim by using the discard option in your /etc/fstab file
```
# / was on /dev/sda1 during installation
UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb /               ext4  ** discard,**errors=remount-ro,noatime,nodiratime 0       1
# /home was on /dev/sdb3 during installation
UUID=5153a0b4-bfe4-4a91-82c9-f6cbfd5b2018 /home           ext4   defaults                                     0       2
# /var was on /dev/sdb2 during installation
UUID=5cae72de-be5c-4586-90ec-c65ce056555b /var            ext4   defaults                                     0       2
# /tmp was made a ram disk after installation
tmpfs                                     /tmp            tmpfs  defaults,noatime,mode=1777
```/dev/sda is a ssd while sdb is a hdd

if you notice i have noatime, it makes a ssd last longer  (nodiratime is a subset of noatime it just makes me feel better with it there)

---

### Post by manfromthezoo on 2012-04-23
Thanks pqwoerituytrueiwoq, but as above I've already edited fstab with this.

Here's mine:

[HTML]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=28f80632-2c49-4b44-8a61-96e0239f9a0a /               ext4    noatime,errors=remount-ro,discard 0       1
# swap was on /dev/sda5 during installation
UUID=a342757e-4e22-4184-8c38-6afd327a74da none            swap    sw              0       0[/HTML]

---

### Post by pqwoerituytrueiwoq on 2012-04-23
i doubt it but dry discard as the 1st option then reboot and see if it is working

---

### Post by manfromthezoo on 2012-04-23
Sorry, I don't understand - what do you doubt?

Good spot - but I had already tried discard as the first option after build. When that didn't work, I noticed others had placed it last, so did the same in case changing the order affected anything.

No cigar.

---

### Post by oldfred on 2012-04-23
I did not set discard right away, so I went back and did this:

Alternate to discard, call fstrim via cron
[http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html](http://opensuse.14.n6.nabble.com/SSD-detection-when-creating-first-time-fstab-td3313048.html)
fred@fred-Precise:~$ sudo fstrim -v /
/: 23267893248 bytes were trimmed

Have you seen these:BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)
Issues with OCZ Vertex II SSD and discard option
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment)

---

### Post by manfromthezoo on 2012-04-24
Thanks oldfred, yes, I had seen those - in trying to troubleshoot this, and when researching what SSD to buy.

I'm starting to wonder if TRIM *is* working - and the weird FFFF structures are the way the Indilinx controller (which the Vertex 4 is based on) denotes the blank sectors. That, or that this test, for whatever reason, gives a false result with this controller - am I right that the vast majority of SSD drives have used Sandforce controllers before?

As yet, the Vertex 4 is so new there are no firmware updates available, btw.

---

### Post by SlugSlug on 2012-04-24
check your kernel version, 

I think trim / discard is only in 12.04


Just to confirm 

> You must have a *kernel* version of at least 2.6.33 

---

### Post by manfromthezoo on 2012-04-24
Hello sluglslug,

11.10 contains a newer kernel by default. Hence, support should be there. For example, as a fully patched 11.10 system, I am running 3.0.0-17 generic.

---

### Post by SlugSlug on 2012-04-24
Sorry, just read over your post again,

I take it the first hdparm you run returns 'random' stuff and then after a sync / rm  your left with ffff's ?


to me that would seem ok, as when my discard was not working I was still left with random stuff after the rm / sync

---

### Post by manfromthezoo on 2012-04-24
> I take it the first hdparm you run returns 'random' stuff and then after a sync / rm your left with ffff's ?


to me that would seem ok, as when my discard was not working I was still left with random stuff after the rm / sync

Yes slug, that's right. First hdparm shows up the random stuff, then after sync and re-check of that range I'm left with the FFFF situation. Good to know you've seen different behaviour when TRIM *isn't working* - perhaps everything is OK, then.

Thanks for sharing that.

---

### Post by wazoo42 on 2012-05-02
I am using gentoo with the 3.3.3 kernel and a vertex 4 128 GB drive, and I see the exact same behavior you do (all f's instead of 0's). The relevant parts of my fstab are given below. 
```

UUID="944a2556-e32c-4aba-9545-14184afa7dc9"             /               ext4            noatime,data=ordered,discard            0 1
UUID="b840774b-d759-48f5-8184-2c74aada4c44" /home ext4 noatime,user_xattr,data=ordered,discard 1 2

```

---

### Post by Shockburner on 2012-07-05
I am using Ubuntu 12.04 64 bit, kernel 3.2.0-26-generic, with a 256 GB OCZ vertex 4 and get the same results (all ffff).

fstab line:
UUID=<uuid> /               ext4    defaults,noatime,discard 0 1

---

### Post by efflandt on 2012-07-06
It is my understanding that SSD is different than a hard drive as far as setting or clearing bits.  A hard drive typically starts out empty (all zeros) and bits can be set or cleared at random.

With flash memory you cannot randomly set bits.  You have to set a block to all 1's and then clear bits that should be zero.  If you did not have TRIM, and wrote to an area where data had been previously deleted (but not actually cleared), it would take some overhead to write all ones and then clear the bits that should be zeroed.

With TRIM enable, deleted blocks are written to all 1's ahead of time, so writing is faster, simply clearing the bits that need to be zeroed.  All 1's would be all f's in hex.

---

### Post by hayvanat on 2012-09-24
Just to inform everyone in case someone else also happens to see "ffff"s instead 0s, 

Ubuntu 12.04 x64 with Vertex 4 I'm also getting all f's instead 0's 

Cheers,

---

