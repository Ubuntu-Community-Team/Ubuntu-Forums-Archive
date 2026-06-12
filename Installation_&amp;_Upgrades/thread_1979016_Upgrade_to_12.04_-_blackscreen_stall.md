---
title: "Upgrade to 12.04 - blackscreen stall"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by aquascrotum on 2012-05-12
Tried upgrading a PC from 11.10 to 12.04, everything went hunky dory up until the prompt to restart after all new packages / cleanup etc had gone through.

The computer hung on shutdown - left it for 10 mins before i powered off.  Then on startup I cannot boot into Ubuntu.

Failure generally occurs when the screen goes to black screen with white text talking about bluetooth and Pulseaudio.

Have tried going into Ubuntu recovery mode but have had no luck there either - going into failsafe graphics, I cannot select any options when I get to the checkbox select box for "Run ubuntu in low graphics mode for just one session" etc.

I really could do with a fix for this quickly, this is my folks machine who have been falling steadily out of love with ubuntu after a number of recent balls ups - cue them being nervous about upgrading and me saying noooo sure it'll be fine.  And now Ubuntu has turned their PC into a brick, I'm feeling the heat - please help!

---

### Post by aquascrotum on 2012-05-12
[http://askubuntu.com/questions/106548/boot-fails-pulseaudio]("http://askubuntu.com/questions/106548/boot-fails-pulseaudio")

Quick edit / addition - The above link describes the same final prompt that I see after trying to boot.

---

### Post by darkod on 2012-05-12
Did you try removing 'quiet splash' from the normal mode entry and trying to boot it, so you can watch the text as it boots. Pay attention to any major errors, for example with video.

That link says it's not really related to pulse audio so I wonder if a video driver could be the culprit.

As far as recovery mode is concerned, what if you try the Drop to root shell, can it load that at least?

---

### Post by aquascrotum on 2012-05-12
> Did you try removing 'quiet splash' from the normal mode entry
How would I do that?

I can boot into what I think Root Shell is by hitting Ctrl+Alt+F1 at the ugly screen, yes.

---

### Post by darkod on 2012-05-12
When the boot menu shows, highlight the normal entry and hit 'e' for edit. That will show the boot lines.

Use the arrows keys to move towards the end of the line starting with linux. Delete 'quiet splash' towards the end of that line. Hit Ctrl + X to boot.

Another option is to enter nomodeset instead of the quiet splash and see if that helps in any way (that's for video issues which this doesn't seem to be but it's worth a shot).

---

### Post by aquascrotum on 2012-05-12
Thanks but doesn't help - just getting a different black screen of text.

---

### Post by darkod on 2012-05-12
But can you notice warnings and errors? with which components, modules, etc?

---

### Post by aquascrotum on 2012-05-12
Running nomodeset I have a fail at "*Starting automatic crash report generation".

After a list of starting / stoppings, I have a message relating to service S25bluetooth and Pulseaudio.

The last message on the screen is Stopping System V runlevel compatibility.

---

### Post by darkod on 2012-05-12
In the grub2 boot menu, is there something like previous versions? Can you try with older kernel, even if it's from 11.10?

Try to boot it without any modification to its boot lines. Just an older kernel.

---

### Post by aquascrotum on 2012-05-12
Have tried all other older kernel versions - the boot hangs in the same place every time.

---

### Post by darkod on 2012-05-12
I'm running out of ideas... :(

---

### Post by aquascrotum on 2012-05-14
Solved in part.  Resorted to a clean install of 11.10 as a short term fix (12.04 Live CD also failed before getting to that), Windows 7 now ordered.

Sorry Ubuntu, this was one muck up too far after what has been a string of breakages for no good reason. It doesn't Just Work any more, and hasn't for a while.

---

### Post by QIII on 2012-05-14
Upgrades somtimes fail when a fresh install does not.

If all of the suggestions above failed, it could simply be a bad download, ISO burn or a condition present in the previous installation.

As humans we are tempted to assume our experience reflects that of everyone else.  However, there are many, many for whom the process has worked just fine, so one cannot say from his own experiences that there is a universal problem.

Nonetheless, yours is certainly a valid reason to be frustrated and use Windows.  There is nothing wrong with that.  But if you have time, it might be helpful to other Windows users to help on a Windows forum where people are having similar problems with Windows.

Use what works for you.

---

