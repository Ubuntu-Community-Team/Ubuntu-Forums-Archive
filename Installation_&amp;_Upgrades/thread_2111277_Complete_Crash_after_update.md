---
title: "Complete Crash after update"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by totallybeachin on 2013-02-01
I need some serious help. 
Firstly, I will say right upfront that I am completely "linux challenged", so please be easy on me. 

I'll start from the beginning; I had never used/seen any Linux computer prior to this point, so there was a little learning curve involved once installed. I learned how to run commands in a terminal, after searching on the net for whatever problems I was  experiencing , (mostly this site), but that is about my extent of "knowledge".

I made 2 partitions on my laptop. 
1 for windows, and 1 for Ubuntu. I noticed over time, that my boot screen *list* kept getting longer and longer, always an Ubuntu xx.xx and then the same line with (recovery mode). (I know this is from updates, I just can't say exactly how many I had, and what my current number is/was. I always just started the computer on the option that was always on the top of the list. 

I had Ubuntu 10.?? (Lucid Linux) installed on my laptop. I usually allowed updates when the update manager popped up and said they were available. After awhile, I stopped doing that. I started noticing sometimes after allowing updates, my computer would go through these times when the screen would just kind of "grey out" and freeze. Sometimes just for a few seconds, sometimes to the point where it was frozen solid to the point I would have to hold down the power button to get it to shut off. 
I noticed just 2 days ago,  on my "update manager" that there was an upgrade available to 12.4 or something to that effect.

I decided to go ahead and upgrade, as I thought maybe a newer version would solve a lot of my other issues, whatever they were. 

Something happened during the install. 
Now, when I try to start the computer, no matter which option I choose, it will load as far as the "purple-ish" start up screen that just says Ubuntu with the little circles below it. It just stays on that screen until I pull the plug. If I choose a "recovery mode" it writes a bunch of stuff on my screen for a minute or so, then just stops like it's waiting for me to give it a command or something, but I have no idea what to do. 

I would have no problem at all doing a complete killdisk and starting from scratch, EXCEPT, I have data that I do not (can't) want to lose, so that can't be an option for me, unless I can get to that data somehow. 

Can someone PLEASE tell me they know what's wrong, (besides operator error, of course......:razz:) and can help me?

---

### Post by AnoPoli on 2013-02-01
Try to hit ALT+F1 to ALT+F6 while on purple screen.
Once you manage to see what happens behind the scenes try to post again.
If you can log in from the console try to continue the upgrade:
***sudo apt-get update***
***sudo apt-get upgrade***
If any errors try:
***sudo apt-get -f install***
first

---

### Post by totallybeachin on 2013-02-01
Thanks for responding.

Ok. Well I managed to get past the purple screen, with your suggestion. Now my "desktop" is just one big terminal.
It says:;
last login (which is wrong) on tty1
/etc/update-motd.d/20-cpu-checker.dpkg-remove: 3: exec: /user/lib/update-notifier/update-motd-cpu-checker: not found
run-parts: /etc/update-motd.d.20-cpu-checker.dpkg-remove exited with return code 127
E: error: BrokenCount > 0run-parts: /etc/update-motd.d/90-update-available exited with return code 255
Welcome to Ubuntu 12.04.1 LTS (GNY/Linux 2.6.32.41-generic 1686)

* Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
angela@angela-laptop: ~$
I typed in here [I][B]sudo apt-get install update
[/B][/I]it asked for my password
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
angela@angela-laptop: ~$ to which I typed 
***sudo dpkg --configure -a'***
and it returned this 
>


[I][B]??? Now what!?

[/B][/I]

---

### Post by totallybeachin on 2013-02-01
I've been playing around a bit, and what I've found is that my computer has multiple partitions on it. I don't know how that works. It's showing a 21gb file system (which is where windows is)
An 84gb file system, where my original Ubuntu install was (is) 
And a 10gb file system where it says the new install is (the 12.4)
However, I tried to run sudo dpkg-reconfigure Ubuntu-desktop and it gave me an error somewhere along the lines that it didn't exist or something. I wish I would have written it down. I inserted my original install CD from 10.4 thinking maybe it had a repair option, which it doesn't but, that is how I was able to get a desktop to load that allowed me to see the other drives. 
I don't know what is going on, or how to fix it. At this point, is there a way to "undo" whatever it did yesterday and get rid of the new 10gb partition that it made, and put it back with the 84gb one?

---

### Post by offgridguy on 2013-02-01
It would help if you could take a screenshot of your partition table and attach it here.

---

### Post by zealibib slaughter on 2013-02-01
instead of [I][B]sudo dpkg --configure -a'
type
sudo dpkg --configure -a
[/B][/I]leave off the ' at the end your terminal thinks that you wish to continue entering a command

---

### Post by totallybeachin on 2013-02-01
> **zealibib slaughter said:**
> instead of [I][B]sudo dpkg --configure -a'
type
sudo dpkg --configure -a
[/B][/I]leave off the ' at the end your terminal thinks that you wish to continue entering a command
This was almost going to work! It started going through all kinds of things, then suddenly, it ended with this message:
Processing was halted because there were to many errors.
Any other suggestions?

---

### Post by totallybeachin on 2013-02-01
I am going to try sudo apt-get -f install

---

### Post by totallybeachin on 2013-02-01
I thought the sudo apt-get -f install was going to work. It said a restart was required, so I used 
sudo reboot
it came back on, acted like it was going to start up, then when to another screen. 

This is the best I can do as far as screen shot.  It is stuck at this point. 
[IMG]http://i135.photobucket.com/albums/q151/totallybeachin/IMG_0580_zps15f32dd1.jpg[/IMG]
[IMG]http://ubuntuforums.org/[IMG]http://i135.photobucket.com/albums/q151/totallybeachin/IMG_0580_zps15f32dd1.jpg[/IMG]

---

### Post by totallybeachin on 2013-02-01
Here's a *screenshot* of my partition table

[IMG]http://i135.photobucket.com/albums/q151/totallybeachin/IMG_0581_zps8e54880a.jpg[/IMG]

---

### Post by totallybeachin on 2013-02-02
Nothing???...............................
from no one!!!
i'm screwed................................lol

---

### Post by AnoPoli on 2013-02-02
Sorry for the delay...
So.... after:
**sudo apt-get -f install**
and if no errors
you must run:
**sudo apt-get update && apt-get upgrade**
if you get errors post back with the errors.
I think that your problem is only a broken upgrade attempt.
i you get past that point i have high hopes.

---

### Post by AnoPoli on 2013-02-02
And another little "secret":
You don't have to pull the plug (most of the times) when you have a "dead" prompt.
You can always login from another tty[1,2,3,4,5,6] with ALT+F[1,2,3,4,5,6]
and instruct your computer to shutdown:
**sudo shutdown -h now**
or reboot:
**sudo reboot**
from there.
tty1 is the console you were working in your screenshots.
You have 5 more.
tty7 is usually reserved for graphics (Xorg)
Also CTRL+C breaks non-responding processes, like the one you mistyped early in your post.

---

### Post by totallybeachin on 2013-02-09
I hope this isn't considered a dead thread. I have not been able to check back since my last posting. 
I did the sudo apt-get -f install and did not get any errors that I am aware of. It did it's thing and returned to a command prompt, so I continued with
sudo apt-get update && apt-get upgrade
and I have more errors than I can count. 
I hope this screenshot can give insight.

[IMG]http://i135.photobucket.com/albums/q151/totallybeachin/IMG_0594_zps0b8bff79.jpg[/IMG]

---

### Post by AnoPoli on 2013-03-26
A bit late, (thought it was a dead thread after a few days...) but to make it clear:
1) No internet access at the time of upgrade ("dhclient eth0" may solve this)
2) sudo apt-get update && **sudo** apt-get upgrade (my mistake, sorry...)
When a command gives errors check first that it was called with sudo in front of it.

---

