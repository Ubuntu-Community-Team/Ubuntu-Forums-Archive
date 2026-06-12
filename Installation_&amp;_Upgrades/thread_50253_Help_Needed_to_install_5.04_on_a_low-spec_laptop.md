---
title: "Help Needed to install 5.04 on a low-spec laptop"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by Ewwmg on 2005-07-19
Little problem, any help would be great. I have a laptop (specs are quite "outdated") anyways . . . I tried putting Linux (warty warthog) on it for the first time.. everything worked great (it was a bit slow, but that was because the laptop was a bit slow) anyways . . . some things happened about a month from the time since putting WW on it . . . I haven't dealt with it since. I just booted it up, last time I came here I was told I should get 5.04, and install it and it should settle over a lot of things. I just finally got the cd today (5.04) I haven't put it in yet, but . . . at regular boot-up, it says "/dev/hda1 contains a filesystem with errors, check forced" . . . anyways, I plan on putting 5.04 on it right now, except one thing: I _need_ to save the things that are on the harddrive already, I understand the installation at that will be a bit more intricate, especially as my knowledge of these things is extremely little. 

Could someone be so kind as to give a few helpful words (or keywords for searching, or even helpful links) to do two things, one: install (or upgrade, if you'd like to say it) to 5.04, while keeping the files that are existent on the harddrive (I don't care of the program settings, or the programs themselves, I just want to have the few document files and such); and two: make the 5.04, this time, a bit faster, so fluxbox, the other little programs, and such on would be cool with me now. I guess I'll try the HOWTO's and such (like this one: [https://wiki.ubuntu.com/InstallUbuntuOnLowMemorySystems](https://wiki.ubuntu.com/InstallUbuntuOnLowMemorySystems) ) except I was hesitant because before that, I need to ensure that the existing files are left alone and safe.

Thanks
-Matt

---

### Post by MatthewMetzger on 2005-07-19
Do a network upgrade with apt-get

I believe detailed instructions are on ubuntuguide.org, but here's my short answer.

sudo gedit /etc/apt/sources.list

change all instances of the word "warty" to "hoary", then save

run from terminal

sudo apt-get update

sudo apt-get dist-upgrade

I hope this helps...

---

### Post by Ewwmg on 2005-07-19
[QUOTE=MatthewMetzger]Do a network upgrade with apt-get

I believe detailed instructions are on ubuntuguide.org, but here's my short answer.

sudo gedit /etc/apt/sources.list

change all instances of the word "warty" to "hoary", then save

run from terminal

sudo apt-get update

sudo apt-get dist-upgrade

I hope this helps...[/QUOTE]

First and foremost: thank you for taking the time to reply.

I am a bit relieved that in that little time that I had Linux, I experimented a lot with CLI and I can mostly get the gist of things, although I am still far from troubleshooting most things to a proper scale. 

The problem here is that I cannot get to the terminal. After the 

[SIZE=1][FONT=Tahoma]/dev/hda1 contains a filesystem with errors, check forced
[/FONT][/SIZE]
it says

[SIZE=1][FONT=Tahoma]Entry '..' in /lost+found/#273483 (273483) has an incorrect filetype (was 1, should be 2).

/dev/hda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
..and some more stuff[/FONT][/SIZE]

Personally, I think I am nowhere near-knowledgeable enough to run fsck manually . . . 

Any hints now would be great =X
Thanks again
-Matt

---

### Post by Lord Illidan on 2005-07-19
Can u backup the doc files on floppy or cd and re-install?

---

### Post by Ewwmg on 2005-07-19
[QUOTE=Lord Illidan]Can u backup the doc files on floppy or cd and re-install?[/QUOTE]
 I have no CD-drive. I would put it on floppy, except two problems: there are well over 60 MB of files that I would like to preserve. Secondly, when I tried the last time, I could not (I think that was mostly due to me being not well-known in that topic  :? )

I think I'll try sending the files over the network and putting it on this desktop (which is my primary computer)

I guess that means I better start looking up some man pages on things relative to the matter . . . hmm, any keywords (to search for) at this or links would be great

Thank you again
-Matt

---

### Post by JayCnrs on 2005-07-19
Have you tried booting into recovery mode. At the grub prompt press the ESC key then choose Recovery Mode.  Hopefully this will get you past the drive check.

---

### Post by Ewwmg on 2005-07-19
[QUOTE=JayCnrs]Have you tried booting into recovery mode. At the grub prompt press the ESC key then choose Recovery Mode.  Hopefully this will get you past the drive check.[/QUOTE]

Just tried it, and it kinda didn't  :-# 
Thanks
-Matt

---

### Post by Ewwmg on 2005-07-19
Sorry that I put this question in this section of the forums, didn't mean to. 

Forum admins, please move this thread to the "Installation Help" section

---

