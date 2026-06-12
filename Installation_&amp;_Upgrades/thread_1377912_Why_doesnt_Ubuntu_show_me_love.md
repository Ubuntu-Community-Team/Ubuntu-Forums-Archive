---
title: "Why doesnt Ubuntu show me love?"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by J.a.M on 2010-01-10
OK so I have been trying to install Ubuntu for about a week now.Last time I tried my power supply blew up.Since then I have gotten a new and better one.I still have been trying to install with no success.

I have tried on both my hard drives, with the regular ubuntu disc and the alternate text based and always get errors.On the regular install i get the "Errno 5" message and on the alternate it tells me to insert the ubuntu disc for no reason while installing.Even though its already in there, and it doesnt let me eject it.So the only option I have is to reboot.

Can someone guide me in the right direction?

PS. 

harddrive 1 is a IDE 160GB 
harddrive 2 is a SATA 320 GB

---

### Post by VideoRoy on 2010-01-10
Can you boot other CDs or DVDs without problem on this computer?

Did you verify the checksums of the ISO files you downloaded before burning them to disc?  If you have another linux running you can check with sha256sum.  If you have Windows you can search around but I have used hashcalc before.

---

### Post by garvinrick4 on 2010-01-10
I would have to make a educated guess with what you have given and say that you are burning your .iso file to your CD at to high a speed. Lower the Burn speed and you will most likely come out with a good Live CD that will be operational. No reason why you should not get your Ubuntu loaded. Use this forum and use Google all you can.

---

### Post by Dayofswords on 2010-01-10
> Last time I tried my power supply blew up
does no one else find this odd?

---

### Post by J.a.M on 2010-01-10
> **garvinrick4 said:**
> I would have to make a educated guess with what you have given and say that you are burning your .iso file to your CD at to high a speed. Lower the Burn speed and you will most likely come out with a good Live CD that will be operational. No reason why you should not get your Ubuntu loaded. Use this forum and use Google all you can.

I downloaded it again after I made this thread through torrent link.Burned at 8x I believe, the slowest setting possible and I still get the error message.

I dont know what to do, I can probably install any other distro besides this. This happened last time in the summer, when I tried ubuntu for the first time.I got it to work some how back then.

I tried three times since making this thread.First try it got to 66% then 69% and third it just gave up around 20%.

The first disc it was probably my fault because I went and used the disc checker and it had one error so I threw that out and made another one (which I am using now) and checked this one and it came out fine.I guess I have to check the checksum on the iso file now

---

### Post by presence1960 on 2010-01-10
[http://ubuntuforums.org/showthread.php?t=1207755&page=2](http://ubuntuforums.org/showthread.php?t=1207755&page=2)  see post #20

Please note the spelling error in red:

In my case was resolved thanks to the fantastic advice from zoomy942 as follows:
1. Boot from the live CD
2. Choose to try Ubuntu
3. Open a terminal window
4. Enter: '[COLOR="Red"]uniquity[/COLOR] --no-migration-assistant'
5. Working install

the command should be ```
ubiquity --no-migration-assistant
```

I used this successfully on a friends computer that kept getting Errno 5.

---

### Post by J.a.M on 2010-01-10
I checked md5 checksum and everything is correct.Gonna try what presence1960 suggested now...

---

### Post by slooksterpsv on 2010-01-10
When I'd get errno 5, it was because of GRUB not interpreting the partitions correctly or knowing what partition Linux was on. I had to make sure to gparted the drive or tell it to install the grub loader specifically on the drive, that's my 2 cents.

---

