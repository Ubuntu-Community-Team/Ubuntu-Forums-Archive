---
title: "how do i install xubuntu? long long time user here"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by pcrussell502 on 2013-11-17
always use the latest version of xubuntu (until now)

always used to run live cd and do a full formatted clean install from there

then for 13.04, i used unetbootin and a fresh .iso of 13.04 and set the bios to boot from usb, and had a great install.  in fact, that's what i'm running this very second as i type... 13.04

time to do 13.10 
and i go through the exact same steps above and every time i try to boot from usb i get "non-system disk".  i tried both a kingston usb and a pny.  how do _most_ people do clean installs of xubuntu anymore?

also, this new login scheme for the forums has caused me to have to start over with a new account even though i've been a member since the mid-2000's... frustrating.

-peter

---

### Post by oldos2er on 2013-11-17
> **pcrussell502 said:**
> this new login scheme for the forums has caused me to have to start over with a new account even though i've been a member since the mid-2000's... frustrating.


For that you need to create a thread in the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123") where an admin can help you.

---

### Post by pcrussell502 on 2013-11-18
nobody uses xubuntu?

i've been using it for years.  

-peter

---

### Post by The Cog on 2013-11-18
I always make a live USB stick with a command similar to this (your input and output filenames may differ):
```
sudo dd if=xubuntu_latest.iso of=/dev/sdd bs=1M
```

---

### Post by pcrussell502 on 2013-11-18
> **The Cog said:**
> I always make a live USB stick with a command similar to this (your input and output filenames may differ):
```
sudo dd if=xubuntu_latest.iso of=/dev/sdd bs=1M
```
  
thanks.  would you say that is the way most folks who install xubuntu do it?  or has xubuntu devolved into such an installation catastrophe that there is no standard way to install it and everybody is more or less on his own to employ whatever trick works?

-peter

---

### Post by The Cog on 2013-11-18
There's no need for drama. It's just how to burn a bootable USB stick. 
I haven't had any luck with the built-in USB stick creator for some years (and don't remember seeing it recently), and I have never used unetbootin that I know of. It's how I've burned bootable Ubuntu sticks for some years. If you're having trouble with unetbootin then perhaps you should try it.

And it's hardly anything to do with installation, any more than having difficulty with a dvd burner would be.

---

### Post by pcrussell502 on 2013-11-18
I used unetbootin to get 13.4 installed.  It worked great.  There is no USB stick creator any more, built in or otherwise... At least none that I can find visually OR  with a search using the app finder... Even though the USB created shows as installed in software center.

I appreciate your help really I do.  But there are very few possibilites to associate with this mystery.  either people aren't doing clean installs of xubuntu (upgrading in place instead), or people aren't using it at all.... Or there is something else that most people are doing that you and I are missing.

By the way, I used unetbootin to make a bootable live stick of puppy Linux and it worked perfectly.  So its not my media.  I admit I didn't do a checksum on my 13.10 .iso but it extracts perfectly (via unetbootin) onto the stick.  Only when I try to boot from it I get "non system disk".

-Peter

---

