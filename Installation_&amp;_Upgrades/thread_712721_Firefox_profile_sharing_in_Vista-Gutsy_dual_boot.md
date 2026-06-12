---
title: "Firefox profile sharing in Vista-Gutsy dual boot"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by ashinshanghai on 2008-03-02
Hi all,

Not a codehead, but Vista drove me crazy and led me to set-up a dual boot with Gutsy (yeah for Gutsy!).

Then I was trying to share my Firefox profile and other data across OSs by following directions from [this Lifehacker posting.]("http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting")

I guess my problem is more with the Windows side than with the Ubuntu side, but here is the issue: From Gutsy terminal I entered:

```
firefox -profilemanager
```

and set up a new profile, pointing to the FF profile on my Vista partition. In Gutsy, FF does not seem to recognize my Windows partition. But worse, now in Windows when I launch FF, I get a message that "FF is already running, but is not responding," and I must either close FF or restart. But restarting does nothing and there does not appear to be a FF process or application when I look in Windows Task Manager. 

I tried uninstalling and reinstalling Windows FF, but this also did not fix it. 

Anyone else have this problem or any ideas on how to fix it so I can get FF running in Windows again (and after that I will try some online bookmark synching instead)? 

Alas, if only Skype would release a video capable linux version I would never have to use crappy MS again...

Thanks.

---

### Post by ashinshanghai on 2008-03-02
Apparently, this is a common problem because Mozilla has a whole support page devoted to it. (Why didn't I look there first???): [http://support.mozilla.com/kb/Firefox+is+already+running+but+is+not+responding](http://support.mozilla.com/kb/Firefox+is+already+running+but+is+not+responding)

Somehow, my Windows FF profile went missing. Not sure why. And still haven't figured out how to link from Ubuntu FF to Vista FF profiles (but it is kind of moot now since the one with all my profile data is gone).

---

### Post by kellemes on 2008-03-02
For this kind of sharing I simply have made a partition, formatted as fat32. Here I have copied the profiles of Thunderbird and Firefox and I point to these profiles from both OS's.
O, and I make daily backups of my profile-folder.. ;-)

Now, I wonder what your question is.. You can't find your profilefolder on Windows?

---

