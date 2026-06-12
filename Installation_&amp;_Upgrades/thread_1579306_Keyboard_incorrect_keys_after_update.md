---
title: "Keyboard incorrect keys after update"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by Newbieuk on 2010-09-21
Hi, hope someone can help.  

Everything has been fine until tonight  - updates have always ran ok.

Automatic update screen appeared tonight so ran it as usual.  

Now the keyboard layout is all wrong, ie backspace key puts a 5 in rather than go back a space,  enter  key  puts / and spacebar  moves 2  spaces also numbers on the right are not correct despite number lock on as usual. What happened to the settings and how can reset keyboard settings.
any help much appreciated as it has taken a age to write this!!
/:(

---

### Post by Newbieuk on 2010-09-21
sorry i am running 9.04

---

### Post by Enigmapond on 2010-09-21
Have you tried System/Preferences/Keyboard/Layout? Just reset it to what you were using...I assume UK. That may kick it back to where it was.

---

### Post by Newbieuk on 2010-09-21
Thanks Enigma pond,  I have tried System/Preferences/Keyboard/Layout and it is set to UK as default and still a problem ie #2 when i type 2 on numeric key board to the right, numbers above qwerty keys ok.

---

### Post by Newbieuk on 2010-09-22
Well I have still had no joy on finding what's wrong with the keyboard.
 
So can anyone let me know if there is a simple way to roll back the changes from the update last night to remove it, like system restore on Windows. Bearing in mind I have very limited experience on Ubuntu or Linux and have never undertaken any "programming" 
 
An help much appreciated.
 
Regards Newbie UK

---

### Post by mörgæs on 2010-09-22
If there was a bug in the update, there is a good chance that it will soon be corrected in another update. 

If you want to solve the problem, you could try waiting a day, boot the machine and then enter

```
sudo apt-get update
sudo apt-get upgrade
```

However, 9.04 is out of support in a month, so rather than solving it it might be better to boot a live CD with 10.04 and install it, if the boot works well.

---

### Post by Newbieuk on 2010-09-22
Thanks mörgæs, 

I shut down the pc completely, rather than just restart, and left it a few hours then started the pc up again and yes it worked the keyboard is now fine with all keys working perfectly.  Thank you.

I am looking to upgrade to 10.04 over the next month and will see how I get on.

Thanks to everyone for all the help and assistance, being not very pc literate, I am sure I will be asking more basic questions as I continue to learn.

Regards

newbieuk

---

### Post by Newbieuk on 2010-11-30
Ho ho, the keyboard issue is back again. 

I have upgraded from 9.04 through 9.10 to 10.04 over the past couple of months and everything has been fine. Today I have booted the pc up to find the same issue, ie space bar puts 2 spaces,  backspace adds a 5 and enter key puts /,  also 2 on the keys to the right adds #2.

I have checked the settings System/Preferences/Keyboard/Layout and it is set to UK as default, tried different English settings ie Canadian still same issue. Have run an update via System/Administration/Update Manager and  restarted but with no luck.
/
Any help much appreciated.
/
Regards

---

### Post by Swagman on 2010-11-30
New Keyboard time ?

---

### Post by mörgæs on 2010-11-30
Again, how does the machine behave when booted with a 10.04 or 10.10 live CD?

---

### Post by geedward on 2010-12-05
My number lock key shut down all the number section, but not numbers above the letters. I have got it back by jiggling the shift key and control key but not sure just how!   I also went into Preferences /keyboard and reset to Layout/options/and default under the desired headings. So far it's working!

---

### Post by Newbieuk on 2010-12-14
Thanks mörgæs and swagman,

I checked a few things out and changed the keyboard, even though it was only just over a year old, and everything is fine now - so guess it was the keyboard after all.

Thanks again

Regards,

newbieuk

---

### Post by mörgæs on 2010-12-14
Good, please mark the thread 'solved' using 'thread tools'.

---

