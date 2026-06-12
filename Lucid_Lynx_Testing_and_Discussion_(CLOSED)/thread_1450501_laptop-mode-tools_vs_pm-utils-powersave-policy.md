---
title: "laptop-mode-tools vs pm-utils-powersave-policy"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Myxb on 2010-04-09
Upon a fresh install of Lucid Lynx beta, I have noticed that the laptop-mode-tools is not installed. Then I tried to install it, but got this:
```
# aptitude install laptop-mode-tools 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  pm-utils-powersave-policy 
The following NEW packages will be installed:
  ethtool{a} laptop-mode-tools sdparm{a} 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 313kB of archives. After unpacking 1,200kB will be used.
The following packages have unmet dependencies:
  pm-utils-powersave-policy: Conflicts: laptop-mode-tools but 1.52-1ubuntu2 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
pm-utils-powersave-policy

Leave the following dependencies unresolved:
ubuntu-desktop recommends pm-utils-powersave-policy
Score is -81

Accept this solution? [Y/n/q/?]
```

Apparently, my system behaves normally now - no constant hdd head parking, no overheating... 

But I wonder should I really install laptop-tools or the pm-utils-powersave-policy if a replacement for it? The both tools seem to control the same thing... Can anybody clarify what is situation in Lucid regarding handling laptops? Thanks!

---

### Post by Miguel on 2010-04-12
I see the same thing, although I dist-upgraded. I think that the issue is that both laptop-mode-tools and pm-utils-powersave-policy do the same thing and are thus incompatible as "daemons".

In my case, I'm pretty annoyed, because I want to change the default values of hdparm -B. I certainly don't want it set at 254 when on AC. In my T400, I've found that 210 is a reasonable compromise (about 3 ticks per hour, but lower heat). Who knows what will happen on battery.

---

### Post by Myxb on 2010-04-16
So I wonder... the pm-utils scripts check laptop-mode files for some of the settings, however in order to install laptop-mode you have to remove pm-utils. Crazy. It is annoying when something new is introduced while old functionality is not supported.

I suspect, however, that there should be a way to control hdparm's through pm-utils. I just did not found how.

---

### Post by Miguel on 2010-04-16
It's possible to replicate the behaviour of laptop-mode-tools by writing scripts to /usr/lib/pm-utils/power.d/. Of course, that requires more knowledge than editing a few values in /etc/laptop-mode/laptop-modoe.conf

Funnily enough, there's a nice script there called 895hdparm-apm which reads and applies your laptop-mode.conf values... if /usr/sbin/laptop-mode exists. Of course, this only happens if laptop-mode-tools has been installed. Not cool.

---

### Post by Myxb on 2010-04-16
On AC the hdparm is 254, on battery power it is 128. The traditional "default" settings. So where does pm-utils takes them anyway? I could not find anything relevant in /usr/lib/pm-utils...

95hdparm-apm script is funny, almost Catch-22-ish. Classic, I just love it. :)

---

