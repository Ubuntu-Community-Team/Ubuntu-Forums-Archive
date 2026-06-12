---
title: "maybe NOT my simple 'idea'(unsearched) an OS install program to copy current drivers?"
date: 2013-10-06
forum: Installation &amp; Upgrades
---

### Post by need4lightspeed on 2013-10-06
HI. I have been around Linux ubuntu since I think 8.04 . .. but I don't 'know all' the terminal commands still (does any one?). I was a Windows person of course but It is just a hobby to examine Open source alternatives and compare every type of software I actually can use. That is a 'prologue' to my actual post.

I want to find out how to install my successful UBUNTU set up & working drivers, performance options(mainly swap amounts for example!**) for any equivalent new installations (Mint, Kubuntu, Xubuntu etc . . .) on my next project PC's or laptops. Assume they're the same drivers for any. Does anyone know how to 'peak' at the installed files & drivers for the same model MOBOs I'll keep building on (not known but probably not intel) on so I can copy the files into a CD or DVD and use them during the install I want on the same MOBOs?(that was vague, sorry)

Its the fact that I got this intel p5SD2 VM - SiS VIA board completely working (video onboard is still not what I need resolution wise) that made me wonder if I could do such a thing on a similar board but u may wonder why would I try this if I didn't have to. I don't plan to do it but hypothetically I might need to on something else that would save my time if doing more than one at a time. I can clarify later but if you know what I am trying to do maybe I can get this SiS VIA intel mobo setup copied and posted somewhere on the net for other developers/users with this same 'frustrating' board needing to get it running with out it taking two months just to finalize an install. I can NOT make the ISO file work personally but some one could look at my set up and say 'oh yeah, that might help a bunch of SiS VIA intel laptop users as well' . . .

That was the main reason for this question . . . 

The other reason is I have a couple boards on the way and I want to actually try to install 13.10 on both but in 3/4 the expected time it will take.(assume I will do the 13.10 install and just figure it out then use the same configs & files as needed but it is not what I am asking here)

It just seemed like this 'idea' would already be instituted and be preferred by users, beginners and developers to have the download available for the MOBO of choice by the ' random geniuses' that completely figured out what was needed, it seems very possible with today's techi-user doing a lot of the tweaking and testing of open source sw . . . why not post the ready to go installation ISO file with the exact drivers you need for YOUR MoBo, made by a simple 'copy program' that turns your OS into an installation version?  (baring the primary video card drivers only, if none onboard right? most audio is onboard default)

Is this already common practice but I just can't see it? I didn't notice mobo specific ISOs files at all over the years accept android set ups I believe . . . IDK.

tia

** USEFUL FOR ANY NEW INSTALL!

THIS BELOW HELPED MY 'START UP' TIMES A LOT & EVERYTHING ELSE, INCLUDING 'SHUT DOWNS'!


**[B][SIZE=3]Install Synaptic, gksu, dconf-tools, Leafpad and GDebi[/SIZE]**[/B]

 1.4. There are some important applications for managing your system,  that aren't installed by default: Synaptic, dconf-tools, gksu, Leafpad  and GDebi.

***Synaptic*** and ***GDebi*** are useful installation tools, which sometimes are more useful than the default Software Center. 

***Leafpad*** is ideal for editing system-wide configuration files by hand. [Much better than the default text editor Gedit]("https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Text-editor-Gedit-shows-irritating-behaviour-when-run-as-root").

Install them all by means of Software Center. Or by the terminal, which is even quicker:
Click on the grey Ubuntu logo (Dash home). Query: [COLOR=#0000FF]terminal[/COLOR]. 
Click on Terminal.
Type (use copy/paste to transport this magical incantation to the terminal):
[COLOR=#0000FF]sudo apt-get install synaptic dconf-tools gksu gdebi leafpad[/COLOR]

Press Enter. When prompted, type your password. Your password will  remain entirely invisible, not even dots will show, this is normal. 
Press Enter again.

**[SIZE=3][B]Decrease the swap use (very important!)**[/SIZE][/B]

 1.5. This is especially noticeable on computers with relatively low RAM  memory (512 MB or less): they tend to be far too slow in Ubuntu, and  Ubuntu accesses the hard disk too much. Luckily, this can be helped.

On the hard disk there's a separate partition for virtual memory, called  the swap. When Ubuntu uses the swap too much, the computer slows down a  lot. 

Ubuntu's inclination to use the swap, is determined by a setting. The  lower the setting number, the longer it takes before Ubuntu starts using  the swap. On a scale of 0-100, the default setting is 60. Which is much  too high for normal desktop use, and only fit for servers.

Check your current swappiness setting:

Click on the grey Ubuntu logo (Dash home). Query: [COLOR=#0000FF]terminal[/COLOR]. 
Click on Terminal.
Type (use copy/paste):
[COLOR=#0000FF]cat /proc/sys/vm/swappiness[/COLOR]

Press Enter.

The result will probably be [COLOR=#0000FF]60[/COLOR].

First install text editor Leafpad (see item 1.3 above), as that's more  fit for this kind of jobs than Gedit (Lubuntu already has Leafpad by  default).

To change the swappiness into a more sensible setting and improve the  cache management as well, type in the terminal (use copy/paste):
[COLOR=#0000FF]gksudo leafpad /etc/sysctl.conf[/COLOR]

Press Enter.

Scroll to the bottom of the text file and add your swappiness and cache  parameters to override the defaults. Copy/paste the following lines:

[COLOR=#0000FF]# Decrease swap usage to a workable level
vm.swappiness=10
# Improve cache management
vm.vfs_cache_pressure=50[/COLOR]

Close the text file and reboot your computer.

After the reboot, check the new swappiness setting:

Click on the grey Ubuntu logo (Dash home). Query: [COLOR=#0000FF]terminal[/COLOR]. 
Click on Terminal.

Type (use copy/paste):
[COLOR=#0000FF]cat /proc/sys/vm/swappiness[/COLOR]

Press Enter.

Now it should be [COLOR=#0000FF]10[/COLOR].

***Note:*** your machine might benefit from an even bigger decrease in swappiness. A useful rule of thumb might be this:
1 GB RAM or more: swappiness at 10
Less than 1 GB RAM: swappiness at 5

---

