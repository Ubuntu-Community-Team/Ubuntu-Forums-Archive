---
title: "Can't tick Synaptic Package Manager"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2008-09-02
Hi all. Installed Ubuntu Studio 8.04 on my desktop (was using Gutsy which was pretty well flawless) about a month ago and now have a bit of time to set it up. And I am getting a headache with one prob after another. I currently have these two issues:

1/ Couldn't see Synaptics Package Manager and a few other things in the **System->Administration** menu. So ... go to **Preferences->Main Menu** and sure enough, not ticked. So I tick it, tick hangs about for a second or two, then unticks itself! Same with Software Sources and anything else that is not ticked in there!

2/ When I go into terminal on all other machines in my house (wife's desktop and my laptop), if I hit the up arrow key, I usually get the last command I entered (save re-typing). What is even cooler is if I keep hitting up arrow, it just keeps going back through the commands I have typed since I have had the computer on for that session. How neat and what a time saver. Not on my desktop UStudio box now though. What I get is this:

```
$ sudo blkid
/dev/sda1: LABEL="MUSTECHHD" UUID="8ADA-12FA" TYPE="vfat" 
/dev/sdb1: UUID="60D8752FD8750496" LABEL="SOUNDS" TYPE="ntfs" 
/dev/sdb5: UUID="1C88764C88762504" LABEL="AUDIOBUP" TYPE="ntfs" 
/dev/sdb6: UUID="24A8779AA8776966" LABEL="JUKEBOX" TYPE="ntfs" 
/dev/sdb7: UUID="0A9C78D99C78C0AD" LABEL="DISK1-MISC" TYPE="ntfs" 
/dev/sdc5: UUID="4E6411F66411E18F" LABEL="RECORD" TYPE="ntfs" 
/dev/sdc6: UUID="8E607CD4607CC48D" LABEL="VIDEOBUP" TYPE="ntfs" 
/dev/sdc7: UUID="88D000A4D0009A98" LABEL="DISK2-MISC" TYPE="ntfs" 
/dev/sdd1: UUID="C870756B7075615C" TYPE="ntfs" 
/dev/sdd3: UUID="87d2c683-36b2-4afa-a792-a62fa9decfac" TYPE="ext3" 
/dev/sdd5: TYPE="swap" UUID="0a2dab87-06b8-4d32-8b1a-7554646adba2" 
/dev/sdd6: UUID="74e4b320-2371-4e9c-8593-6b33e3266056" TYPE="ext3" 
$ **^[[A**
```The part at the end (in bold - [[A ) is the result of hitting the up arrow key - just the code for the key I suspect. I should be getting the last command I used, in this case 'sudo blkid' (which is just an example - nothing wrong there). Another thing which could be the reason for this and a few other probs is that all I get is '**$**' at the terminal cursor. I should be getting '**ustudio@ustudio $**' first, or something similar. Also, I can change directories, but still only get the '$', not, for instance, 'ustudio@ustudio. media $' or whatever directory I have cd'ed to. ???.

Any and all ideas or suggestions more than appreciated and thanking you in advance. :)

---

