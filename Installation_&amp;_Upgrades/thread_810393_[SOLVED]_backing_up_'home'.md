---
title: "[SOLVED] backing up 'home'"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by lightnin on 2008-05-28
Hi

How do I back up my home directory ?

I have a failed Hardy upgrade and I want to go back to Gutsy
I want to keep all my settings etc

I have a live CD and an external vfat drive that I can write to

when I try to copy my home directory across I get errors for a few files

what command can I use to copy a directory and all sub files - whilst listing all errors.

I have tried sudo nautilus and I just get an error log, but no file names.

Thanks

Rich

---

### Post by Dan++ on 2008-05-28
In terminal, go to your home directory, and type

```
sudo cd -r -v * <DESTINATION PATH>
```

Should

---

### Post by lightnin on 2008-05-28
Thanks Dan

that 'seems' to have worked !

I guess I will find out when I re-install 7.10 :0

---

### Post by Dan++ on 2008-05-28
Great! If you have any problems post back here, but I've used a method like that before recently and had no problems,  but I was moving from Hardy to Hardy. You probably want to make sure there aren't any redundant hidden folders in there with settings for programs which either don't apply to versions made for Gutsy, or just you generally don't need any more. You can show hidden files in Nautilus with View->Show Hidden Files if you didn't already know that :)

Glad I could help :)

---

### Post by lightnin on 2008-05-28
I didn't already know that !

I have done an install and tried to copy my files back

they seem to have copied - but now i am not the owner and I cant chown - 'invalid user' ????

can you only chown to the user you are logged in as ?

---

### Post by lightnin on 2008-05-28
sorted now - I logged in under a failsafe terminal session and changed the owner back to me.  then everything (most things) is back to normal

Thanks again

Rich

---

### Post by lightnin on 2008-05-28
oh - just to add , Ive gone back to gutsy. I will leave hardy well alone until there is more positive feedback around here !  should have checked before I clicked upgrade really !!!!!!

---

### Post by Dan++ on 2008-05-28
Excellent, glad it went okay. I didn't realise there was any negative feedback to be honest. I've had no problems. Then again, I hadn't used Gutsy.

---

### Post by lightnin on 2008-05-28
just have a look through the install/upgrade forum - load of fails and hanging systems etc etc lots of people not happy with hardy.  it seems there is one kernal release that is bad ???

---

