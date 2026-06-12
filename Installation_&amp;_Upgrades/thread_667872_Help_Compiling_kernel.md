---
title: "Help Compiling kernel"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by blackenedbloodx on 2008-01-14
hey i need to downgrade my kernel from the one that came with the Ubuntu CD because of the kacpid problem. i read that it can help. but anyway i am following the steps at 
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)


and when i get to the command
  bzip2 -dc /usr/src/patch-2.6.19-rc4.bz2 | patch -p1 --dry-run
i get this

> 
t.c.rej
patching file drivers/cpufreq/cpufreq.c
patching file drivers/cpufreq/cpufreq_ondemand.c
patching file drivers/cpufreq/cpufreq_stats.c
Reversed (or previously applied) patch detected!  Assume -R? [n] 
Apply anyway? [n] 

what is this? anything i type ends up right back to these prompts.

---

### Post by jeffus_il on 2008-01-15
You may be able to downgrade the kernel using synaptic, open synaptic search packages like "linux-image", see the version numbers, choose one older than your current one, your current one is "uname -a" at command prompt, install, reboot choose an older kernel at the grub menu, Good Luck!

---

### Post by blackenedbloodx on 2008-01-15
No way man. its the one i have. no earlier ones.

---

### Post by Partyboi2 on 2008-01-15
I noticed that patch is optional, do you need it?

---

### Post by blackenedbloodx on 2008-01-15
yes i have runaway processes that take up 100% of my CPU for no reason. i have heard that downgrading the kernel solves it but if anyone knows how please tell me!! i feel like i'm running Vista Ultimate on a computer with less than 10 megs of RAM!!!  :'(

---

### Post by Partyboi2 on 2008-01-15
What kernel number are you trying to downgrade to? Also what version patch are you trying to apply to this kernel?

---

### Post by jeffus_il on 2008-01-15
Please post the names of the processes taking up 100% cpu.

---

### Post by blackenedbloodx on 2008-01-15
the processes are kacpid and xgl and kacpid_notify. i have seen where acpi=off in the menu.lst in the grub folder help w/ kacpid, but then my wireless doesn't work.

i am running 2.6.22-14 and i heard of a case someone had the same problem and downgraded to 2.6.17-10 so i am trying to downgrade to that. i have no clue what patch it is. i am just trying to follow the instructions of the link i posted at the start but that weird prompt always comes up. i tried every possible response to it like "y" "n" "R" and others and it still pops up. what is it? or at least how can i solve the CPU problem?

---

### Post by jeffus_il on 2008-01-15
I am not a KDE user but you could try removing the kacpid daemon from your session manager.

---

### Post by jeffus_il on 2008-01-15
I just googled kacpid.
Seems to be a very widespread problem across many Linuses, 
here's the first one:
[http://www.linuxquestions.org/questions/linux-software-2/kacpid-eating-cpu-99-cpu-time-213429/](http://www.linuxquestions.org/questions/linux-software-2/kacpid-eating-cpu-99-cpu-time-213429/)

---

### Post by blackenedbloodx on 2008-01-15
yea i saw that when i first figured out the problem. i tried to install acpi and it was already there. (said 0 upgraded etc.) and i cant kill the process. what really sucks is that i did solve it by going to /boot/grub/menu.lst and putting 

acpi=off apm=off 

in my kernel line. that worked but if im not mistaken that is the PCI slot. and when i booted up i couldnt connect via wireless.

and by the way thanks for responding to my call of distress :)

---

### Post by blackenedbloodx on 2008-01-15
hey i been thinking.

One major boast Linux has against Windows is that its safe from malware right? well with the increasing popularity of linux, it is more likely that it has a virus than before because we used to say the average consumer that buys a computer has windows. well Dell as we all know ships ubuntu computers. in my opinion, viruses are more probable now than before. and i also heard that Vista is the last windows because linux is going to take on microsoft, at least thats what i heard... or maybe a windows junkie gets pissed off at that boast and makes one. i know its not that likely but all the developers aren't really concerned with it and it is possible...

any thoughts of this?

---

### Post by jeffus_il on 2008-01-16
You could try do drop the "acpi=off" and find a local solution to your wireless problem, maybe looking at bios settings and at the driver itself, may be simpler with less side-effects.

---

### Post by blackenedbloodx on 2008-01-16
...how would i do that? please make it simple i am still a Linux-noob :)

---

### Post by jeffus_il on 2008-01-16
You would have to drop the "acpi=off" from your boot, then reboot and describe here the error messages you get from you wireless driver, maybe from dmesg or the system logs.

How did you get to the "acpi=off" solution?

---

### Post by blackenedbloodx on 2008-01-16
i forget exactly where i got that. but yea i dont get any error messages other than when i boot up something about ICQ is not recognized. its weird because i can see the other wireless network nearby and i have a signal but i cant connect to mine. and no i dont have the password to the other one :P

---

### Post by jeffus_il on 2008-01-17
What program do you use to make the wireless connection.
Drop the acpi stuff at boot and let's fix up the wireless connection.

---

### Post by blackenedbloodx on 2008-01-17
umm. no program... i just detect it and enter the password... what program would you suggest and how to do it?

---

### Post by jeffus_il on 2008-01-18
Do have a little icon with dots circulating round it when you start up? If you click on it you may see Metwork Manager somewhere?

---

### Post by blackenedbloodx on 2008-01-18
yes thats how i normally log into the network but if i turn off the acpi then it doesn't work

---

### Post by jeffus_il on 2008-01-18
click on that icon and use the manula setup, not the automatic one (or roaming)

---

### Post by blackenedbloodx on 2008-01-18
yea i tried that too. it just wont detect the signal

ok bear with me dont log off ill try turning it off and tell you exactly what happens and any errors

EDIT: ok after it says GRUB loading stage 1.5 at boot it says something like

[0000] BIOS bug, no ICQ (input - i think), using default mtable

---

### Post by jeffus_il on 2008-01-18
Ok, stop the networkmanager:
In a terminal:
```
sudo /etc/init.d/networkmanager stop
```

edit the networking interfaces file:
```
sudo nano /etc/network/interfaces
```

It should look something like this:
```
auto lo
iface lo inet loopback

auto ath0 # yopur device here
iface ath0 inet dhcp
wireless-key s:***** # if you use wep
wireless-essid <your access point>

```

restart networking

```
sudo /etc/init.d/networking restart
```

Watch the output for errors , post.

Hope I didn't miss something, did it from memory, am a bit senile!

---

### Post by blackenedbloodx on 2008-01-18
lol its cool. thanks im trying it now

EDIT: ok all it says is this nothing is after it

auto lo
iface lo inet loopback

---

### Post by jeffus_il on 2008-01-18
use```
 iwconfig
``` to see your network device, post the output here.

Have you set up any security on you access point, password? keys? etc.??

---

### Post by blackenedbloodx on 2008-01-18
lol this might be my whole problem. btw thats my stepmom's name i turned 18 like 2 months ago :P

note: there is no space in "thr: off" but it kept making a smiley lol

> 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Erica's Home Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:2F:49:47:CE   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Link Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---

### Post by jeffus_il on 2008-01-18
You may be connected, can you browse the internet?

---

### Post by blackenedbloodx on 2008-01-18
yeah, oh u mean use those commands when i am acpi=off? ok then brb

EDIT: ok yea the output is still the same and i keep hearing the login noise when im logged in *click click click click click click*

??????????????????????


oh and the boot says no ICQ ENTRIES not inputs

---

### Post by blackenedbloodx on 2008-01-18
> **jeffus_il said:**
> I am not a KDE user but you could try removing the kacpid daemon from your session manager.

i just noticed you said this
i use gnome...:confused:

---

