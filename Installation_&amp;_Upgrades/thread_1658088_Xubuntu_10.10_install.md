---
title: "Xubuntu 10.10 install"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by mark_E on 2011-01-02
Hi,
 
Completely new to linux so i'm probably doing something stupid :) but i'm having trouble installing Xubuntu 10.10 onto an older PC (1.7G athlon, 500M ram, 80G harddrive - using entire harddrive for linux, formated/setup/whatever by xubuntu install).
 
**The issue is that I can't get past the 'Who are you?' screen because the 'Forward' button never highlights.**
 
I have green dots next to all the text boxes presumably implying that the entries are ok. I've set it to log in automatically but have tried all combinations. The progress bar along the lower section of the window says 'Ready when you are'. The "DOS" type box (sorry long time pc user lol) under this states 'ubuntu ubiquity[2649]: switched to page usersetup'
 
I've done a search but can't find this particular issue.

---

### Post by SnickerSnack on 2011-01-02
You might try using the "alternate" installer.  It uses a non-graphical interface which can work better with old hardware.  I've only installed xubuntu once, so I don't remember if what you're describing comes before or after installation is complete.

Also, if you do reinstall, it's a very good idea to make two partitions, one for the root directory, and one for the home directory.  The main benefit is that it's easy to reinstall of try a new linux distribution without touching the home directory.

---

### Post by mörgæs on 2011-01-02
Hi, welcome to the fora. 

The user name must be in small letters only. The 'Forward' button highlights, when the name is accepted.

---

### Post by mark_E on 2011-01-02
thanks for your replies guys. I see now someone else has the exact same problem i do.
 
I'm pretty darned sure that i tried everything in lower case lettering. My trouble now is that i can't get back to that point (to double check) because the install seems to crash trying read any cds that i burn. At this stage i think i'll try downloading the 'alternate' iso and restart from scratch.
 
just a note re: the 2 partitions . . . so you put the operating system on the root and any user modified files on home?
 
edit: his problem has turned out to be the caps thing :) since this reply.

---

### Post by jkenny7512 on 2011-01-02
I am having the same problem. The installation is hung up on the "Who are you" page. My name. computer name, and user name all have green checks next to them. 
I have tried both checking "Log in automatically" and "Require my password to log in" but the forward button still does not highlight.
Any ideas on how to fix this problem?

---

### Post by mark_E on 2011-01-02
well i thought i'd try 1 more time with another dvd drive before downloading another iso. :)
 
i can confirm all entries were in lower case.
 
i managed to get the forward button 'ungreyed' not 100% sure on steps involved - the order is important tho. 
 
went something like this - enter a password, then select 'password required', then select encrypt. I have subsequently unchecked these to log in automatically and the forward button remained 'ungreyed'.
 
install is now continuing . . .
 
hope this helps u jkenny - like i say not 100% sure on order so u mite have to muck around with it a bit

---

### Post by Mykhaylo on 2011-02-01
> **mörgæs said:**
> Hi, welcome to the fora. 

The user name must be in small letters only. The 'Forward' button highlights, when the name is accepted.

Thanks! I came across this thread with the same problem and the username having to be in small letters was the problem. They should really correct this problem, allowing users to use capital letters in their usernames!

---

### Post by mörgæs on 2011-02-01
It will be corrected in 11.04 in that sense, that the user will see a message (rather than just a grey button) if he is trying to enter an invalid user name. 

If it was allowed to have capital letters, a lot of confusion would occur: John, john and JohN being three different users...

---

