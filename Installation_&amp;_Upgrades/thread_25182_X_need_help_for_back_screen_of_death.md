---
title: "X need help for back screen of death"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2005-04-09
Hi I have tryed installing Ubuntu about 5 tiems and keep getting an x error and my sscreen wornt work and it wont let me in which makes me think it is running but not showing. I have nv graphics but also I have a ati tv tuner card and am wondering if this mat cause a problem? My monitor is an old bridge KTX.

---

### Post by jordanau on 2005-04-09
[QUOTE=Omnios]Hi I have tryed installing Ubuntu about 5 tiems and keep getting an x error and my sscreen wornt work and it wont let me in which makes me think it is running but not showing. I have nv graphics but also I have a ati tv tuner card and am wondering if this mat cause a problem? My monitor is an old bridge KTX.[/QUOTE]


What is the error?
Describe what you mean by screen not working
Won't Let you in? Can you log in to the terminal with no X??
Also if you can paste your Xorg.0.log file, it will be very helpful.
Also what exactly is the card you have?

Answer those questions to increase the chances of someone knowing what to do. 

If you don't already know, the Xorg.0.log path is in /var/log/Xorg.0.log

---

### Post by Omnios on 2005-04-09
When I installed it looked ok. Then at the end of the first boot it tryes to load gmone at which point X sever fails and does not give a lot of info jjust saying to lauch x when it is fixed.  I tryed rebooting again and the error does not show but I just get a blank black screen and can't get the log on prompt. I have a Gforce2 nvidia 3d card. I also have a ATI tuner card 'just a tv tuner but am wondering if its causing a conflic. 

Im a total Linux Newb and dont even know the command prompts yet.

Basicly it loads screen goes to a slightly different black and im locked out from cammands almost as if its running in the computer but not showing on the screen

---

### Post by Omnios on 2005-04-09
K managed to get into command line but only right after insalling
The error messages are
Log file: "var/log/Xorg.0.log"
using config file: "etc/11/Xorg.cofig
skipping usr/X11R6 lib/moduals/
extentions/LibGLcore.a:M_debug_clip.0." No sybols found
"" "" "" "" _norm.0 No Symols found
"" "" "" "" _Xform.0": No sybols found
EE NV(0):No valid modes found
EE Screens(s)found but none of them have a usable configuration
Fatal Server Error:
No screens found.

I took out the ati tv tuner card but that made no differense. 
Excuse any errors I had to jot this down on paper then write it into forum hope this helps.

---

### Post by j j on 2005-04-09
[QUOTE=Omnios]Basicly it loads screen goes to a slightly different black and im locked out from cammands almost as if its running in the computer but not showing on the screen[/QUOTE]

I have the same problem - X is actually running but the screen is black. I can alt+ F1 to get to console. If I knew enough about "vi" I'd edit my config files... but I don't. I'm a Midnight Commander junkie. I tried apt-get install mc -- no luck. Any suggestions? I'd really like to give Ubuntu a try. Thanks..

---

### Post by Omnios on 2005-04-09
Noticed something in the error which may pertain to a drive. Currently I have master running win xp and the slave running Linux not shure if this makes any difference

---

### Post by az on 2005-04-09
[QUOTE=Omnios]K managed to get into command line but only right after insalling
The error messages are
Log file: "var/log/Xorg.0.log"
using config file: "etc/11/Xorg.cofig
skipping usr/X11R6 lib/moduals/
extentions/LibGLcore.a:M_debug_clip.0." No sybols found
"" "" "" "" _norm.0 No Symols found
"" "" "" "" _Xform.0": No sybols found
EE NV(0):No valid modes found
EE Screens(s)found but none of them have a usable configuration
Fatal Server Error:
No screens found.

I took out the ati tv tuner card but that made no differense. 
Excuse any errors I had to jot this down on paper then write it into forum hope this helps.[/QUOTE]

You have a (simple) X problem.  Your hardware is misdetected.

Try 
sudo dpkg-reconfigure xserver-xorg

I know nothing about anything other than a simple svga video card, so maybe someone with an nvidia can help you more.

If it is any encouragement, you are very close!

---

### Post by az on 2005-04-09
[QUOTE=j j]I have the same problem - X is actually running but the screen is black. I can alt+ F1 to get to console. If I knew enough about "vi" I'd edit my config files... but I don't. I'm a Midnight Commander junkie. I tried apt-get install mc -- no luck. Any suggestions? I'd really like to give Ubuntu a try. Thanks..[/QUOTE]


Mc is in universe.

Use nano

sudo nano /etc/apt/sources.list

CTRL - O to save
CTRL - X to exit

---

### Post by Omnios on 2005-04-10
K got into sudo......... and played around with a hole bunch of settings and still nata also noticed out of the corner of the eye that after the cd and it started setting up there was a default config error but it kept going so im asuming its not an issue unless I have a corrupt download. It seems to detect the nv etc and the pci address so im assuming it has something to do with the screen resalution or soething to do with that as i try to run start x and still get the errors after manualy configuring. Also red it will try to maximize res etc which may be the problem. Im such a Linux newb but im learning and thats why I want learn Linux so bad as its fun. 

Another note my video card has a secondary tv out if that helps any?
Any ideas?

 I have a 6 year old Gridge BM17c 17" monitor but it always ran under default settings though.

Thought of a possible problem in xp it only gives me 16b and 32b graphics quality but in linux its trying to use 24bit could that be causing this, time to try installing it again. Time to try installing it again lol

 Did some reading on the web that suggests it may be the monior they said something like x 4 config or something for red hat not shure how it works in Ubuntu

** I have a quick question? After going through config it boots you out to a templet do you have to save this and how? ](*,) **

---

