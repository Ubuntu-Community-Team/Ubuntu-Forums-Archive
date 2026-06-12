---
title: "Pentium M undervolting - possible to get into Dapper?"
date: 2006-03-18
forum: Installation &amp; Upgrades
---

### Post by Muffe on 2006-03-18
I have an Acer Travelmate 3002 WTMi laptop with a Pentium M 740 1,73 GHz CPU. Previously, the fan was nearly always running (at 800 MHz), and it did create a lot of noise... The battery time was between 100 and 120 minutes depending on the system load.

A few days ago, I found an [article]("http://gentoo-wiki.com/index.php?title=HOWTO_Undervolt_a_Pentium_M_CPU&oldid=67226") on the Gentoo WIKI, and thought: that is something I want to test. I also found a [post]("http://www.ubuntuforums.org/showthread.php?t=97043") on this forum, about the same topic.

Today, I downloaded the newest kernel from kernel.org, applied the patch and compiled the kernel. I have now booted into my new kernel, and the fan is very rarely spinning. I would also think that the battery life is extended by 10-30 minutes, but I have not tested that myself (I haven't had time to that).

I have tried to apply this patch into the standard Dapper kernel sources (apt-get install linux-headers-2.6.15-18), but the speedstep-centrono.c file is not present, so I can't patch it.

Is it possible to get this patch integrated into to the standard Dapper kernel? The default voltage values are the official Pentium-M values, and the CPU is not automatically undervolted if you apply this patch. The undervolting has to be done manually after each boot (you can of course write a script to do it), so if you don't want to undervolt the CPU, you don't have to do anything.

Where do I post a request for integrating a patch like this into the kernel? I don't consider it to be a bug, so I dont't know where to post it... This patch would make a laptop-owners life a lot easyer...

Thanks for all replies.

---

### Post by opera118 on 2006-03-18
> **Muffe]I have tried to apply this patch into the standard Dapper kernel sources (apt-get install linux-headers-2.6.15-18), but the speedstep-centrono.c file is not present, so I can't patch it.[/QUOTE]

The kernel-headers is exactly what it says - the headers. In C source code you have c-files and h-files (header files). The header files only contains a declaration of the functions used in the c files, not the actual source code.
So downloading the source from kernel.org is the right way. I do it, many people do it.

[QUOTE=Muffe]Is it possible to get this patch integrated into to the standard Dapper kernel? The default voltage values are the official Pentium-M values, and the CPU is not automatically undervolted if you apply this patch. The undervolting has to be done manually after each boot (you can of course write a script to do it), so if you don't want to undervolt the CPU, you don't have to do anything.[/QUOTE]

[QUOTE=gentoo-wiki]Warning: Use at your own risk. As far as I know it has been tested only on a few computers. It may very well permanently damage your CPU. I give no guarantee as to whether it will work for you.

Changing the voltage of a Pentium M CPU is not recommended because it can make it run out of its specifications. [/QUOTE]

You think ubuntu would support this?  said:**
> Where do I post a request for integrating a patch like this into the kernel? I don't consider it to be a bug, so I dont't know where to post it... This patch would make a laptop-owners life a lot easyer...

You could, if you really want, send a mail to lkml (it's public afaik) and ask the kernel people about it.

I'm off for some investigation in this... I'm literally burning my fingers on parts of my laptop.

---

### Post by Omer on 2006-03-18
So you'll probably want linux-source package.

---

### Post by unf on 2006-03-18
I have a Acer Aspire 5021Wmli in windows I use rmclock  to undervoltage because it is very loud at full speed 1.6Ghz. Of course cpu scaling works but still loud.

---

### Post by Muffe on 2006-03-18
Thank you. Scince the battery meter didn't work with my self-compiled kernel with sources from kernel.org, I'm now building from the ubuntu-supplied linux-sources package. I'll report the result.

---

### Post by Muffe on 2006-03-18
I have now grabbed the kernel sources with apt-get, applied the patch from Gentoo WIKI, and compiled the kernel with standad Ubuntu configuration.

The result is good. The battery meter does work (it didn't work with the standard kernel from kernel.org), and the best of all: the battery life is extended with approximeatly 25 minutes at 700 mV at 800 MHz (11,1 volt 4800 mAh battery). The fan does not spin up so often as before , and when the machine idles for a long time, the fan does not spin at all. I have made a simple bootscript that applies the voltage settings at boot, so you don't have to apply them manually after each reboot.

I think the Ubuntu developers shoud consider applying this patch into the standard Ubuntu kernel. The new users and those with normal desktop PC's won't notice any difference at all, but the more advanced laptop users who choose to undervolt their CPU, will get a more silent laptop and linger battery life without needing to recompile the kernel.

---

### Post by quaddy on 2006-03-18
hi,

i think you dont actually have to compile a whole new kernel.
keeping in mind that the kernel shipped with ubuntu makes use of modules I simply got the kernel-source with apt-get, applied the patch and only recompiled and installed the modules. ( make modules and make modules_install | maybe its prossible to only compile the centrino-speedstep-module but i dont know how, would save some time) 
worked well for me but may lead to problems that i dont have any idea of :)

rebooting after that should do the trick ( reloading the module should also work but the module wouldn't reload because it was in use by other modules )

My personal opinion on including the patch to the shipped kernel is, that it wouldn't be a good idea because you can easily kill your CPU with this and only people who know what they're doing should work with this.

---

### Post by patrickfromspain on 2006-03-18
I don't understand something... why this undervolting? Isn't speedstep enough???

I'd like to have some more info on this... why undervoltage the cpu and not just let it run at, say, 50% of it's gigahertz?

Thanx

---

### Post by shu on 2006-03-18
I have Pentium M 1.73 and I can have it running at 800MHz (it won't go any lower). However, while running at 800Mhz it requires 900mV voltage by default and you can - thank to gentoo patch - force it to take let's say 800mV? 700mV?  The lower the voltage, the longer battery life with the same cpu power.

---

### Post by opera118 on 2006-03-18
I just think I love you, Muffe. Didn't even know about this whole concept.

So, since I'm using my own kernel anyway, patching it for this was simple. And it works like magic. I used windows rmclock and prime95 to stress test what lowest voltage I could get.

patrick, speedstep is not enough, on many laptops (such as mine) the fan is a nightmare, sounds like a dog barking, and the laptop can get really hot. this is because the processor runs at a rather high voltage level. This has nothing to do with frequency actually.

My cpu had this config (ignoring mid-steps)
1.6ghz: 1.356 V
0.8ghz: 0.988 V
I have successfully made it run with:
1.6ghz: 0.956 V
0.8ghz: 0.700 V

So it uses less power on full speed now, than it used to on half speed ;) Not that I've used the battery on this machine yet, but I'm sure the battery time will improve by some tenths of minutes.

The kernel dudes really need to implement this into the mainstream kernel...

---

### Post by klahjn on 2006-03-18
I'm thinking that it may be kept outside the mainstream, for the simple fact that the n00bs shouldn't be hacking away at this stuff rendering hardware useless by typos or something....or misinformation.  Just a protective measure.  The ones that need that type of patch, probably know already how to compile in support, or are going to research and learn, as i believe it should be.  Not that i would like it difficult for you guys, but i personally would feel more safe if it were more difficult for n00bs to be able to undervolt thier processor to say....something like 3mV or something.

---

### Post by opera118 on 2006-03-19
[QUOTE=klahjn]I'm thinking that it may be kept outside the mainstream, for the simple fact that the n00bs shouldn't be hacking away at this stuff rendering hardware useless by typos or something....or misinformation.  Just a protective measure.  The ones that need that type of patch, probably know already how to compile in support, or are going to research and learn, as i believe it should be.  Not that i would like it difficult for you guys, but i personally would feel more safe if it were more difficult for n00bs to be able to undervolt thier processor to say....something like 3mV or something.[/QUOTE]

n00bs =)
Funny, that term is used seriously by most psuedo-n00bs...
Anyway, I did some googling on this, and it seem _very_ common on windows. The common way of testing is by using prime95 (or similar) to see when calculations are erronous. The danger in this seems, to me, to be more or less "don't blame me if...". I really doubt if anything could ever break. The worst thing is if you start lowering it at too large steps in a time and go to far too low voltages. It hung my machine a couple of times, but reboot and go again at not so very low voltages... no problem. I really enjoy a much more silent and cold machine.

And btw, I dunno if "n00b" is even appropriate here. There are probably very few people who knows about what the side effects are. I doubt if any of the windows-hw-forum-people know about it. I've been schooled that in modern processors, the frequency is pretty proportional to the square of the voltage, and I've read some IEEE articles about it. I think I would be one of those understanding it, but I'm a bit amazed that the voltage can be altered [this much] at fix frequency.

---

### Post by Muffe on 2006-03-19
For those of you who have applied this patch, I'll post the boot scripts I use for undervolting my processor at boot:

/etc/default/undervolt (configuration file - **important: modify according to your processor!**)
```
#!/bin/sh
# /etc/default/undervolt
#
# Written by Håkon Strandenes, 2006
#
# Distributed under the terms of the GNU General Public License version 2
# as published by the Free Software Foundation or any later version (at your
# option.

# Is undervolt activated? [yes/no]
ACTIVE="no"

# switch back to default voltages if undervoltage is stopped? [yes/no]
SWITCH_BACK="yes"

# voltage table sysfs interface
VTABLE_SYSFS="/sys/devices/system/cpu/cpu0/cpufreq/voltage_table"

# Pentium-M 740 1,73 GHz default voltages
DEFAULT_VTABLE="1356,1212,1100,988"

# Pentium-M 740 1,73 GHz lowered voltages
MOD_VTABLE="1052,844,764,700"
```

/etc/init.d/undervolt (the boot script)
```
#!/bin/sh
# /etc/init.d/undervolt
#
# Written by Håkon Strandenes, 2006
#
# Distributed under the terms of the GNU General Public License version 2
# as published by the Free Software Foundation or any later version (at your
# option.

# Include config file if available
if [ -f /etc/default/undervolt ] ; then
    . /etc/default/undervolt

    case "$1" in
        start)
            if [ $ACTIVE = "yes" ]; then
                echo "Applying custom vtable:"
                echo ${MOD_VTABLE} > ${VTABLE_SYSFS}
            else
                echo "Undervolt is not activated."
            fi
        ;;
    
        stop)
            if [ $SWITCH_BACK = "yes" ] && [ $ACTIVE = "yes" ]; then
                echo "Restoring standard vtable:"
                echo ${DEFAULT_VTABLE} > ${VTABLE_SYSFS}
            fi
        ;;
    
        restart|force-reload)
            echo "Restoring standard vtable:"
            echo ${DEFAULT_VTABLE} > ${VTABLE_SYSFS}
            
            if [ $ACTIVE = "yes" ]; then
                echo "Applying custom vtable:"
                echo ${MOD_VTABLE} > ${VTABLE_SYSFS}
            else
                echo "Undervolt is not activated."
            fi
        ;;
    
        *)
            echo "Valid options: start|stop|restart|force-reload"
        ;;
    esac

else
    echo "The config file does not exsist. Please make one." 
fi
```

Remember to run 'update-rc.d undervolt defaults' to make it run at boot... 

I'm not very experienced with shell scripting, so please tell me if any of you find any mistakes in my scripts.

Maybe I'll write a howto somewhere...

---

### Post by opera118 on 2006-03-19
I put my own little script directly in /etc/rc2.S (linked to init.d tho).

But anyway, my voltages are weird, but seems to work. What I initially have is:
"1356,1244,1116,988,4780,4780,4780,4780,4780,4780,4780,4780"
Have no idea what that 4780 is, but I replaced it with my own max-voltage instead... Can't use just 4 values which I'd like... It probably has to do with ACPI reporting many crazy values out of nowhere. I run this instead with no problems (so it probably does for others):
"956,860,764,700,956,956,956,956,956,956,956,956"

---

### Post by Jasman on 2006-04-04
[quote=Muffe]I have now grabbed the kernel sources with apt-get, applied the patch from Gentoo WIKI, and compiled the kernel with standad Ubuntu configuration.

The result is good. The battery meter does work (it didn't work with the standard kernel from kernel.org), and the best of all: the battery life is extended with approximeatly 25 minutes at 700 mV at 800 MHz (11,1 volt 4800 mAh battery). The fan does not spin up so often as before , and when the machine idles for a long time, the fan does not spin at all. I have made a simple bootscript that applies the voltage settings at boot, so you don't have to apply them manually after each reboot.

I think the Ubuntu developers shoud consider applying this patch into the standard Ubuntu kernel. The new users and those with normal desktop PC's won't notice any difference at all, but the more advanced laptop users who choose to undervolt their CPU, will get a more silent laptop and linger battery life without needing to recompile the kernel.[/quote]

Can you tell me which patch you're referring to? I tried this and the patch and rebuild both bombed out. I have linux-phc-0.2.1-kernel-2.6.15.patch. Thanks.

---

### Post by xrado on 2006-04-05
Short tutorial howto applay this patch and get it working, would be great.
I'd also like to reduce the fan noise on my travelmate 4104.

---

### Post by ShaLouZa on 2006-04-09
+1

I'm a n00b when it comes to Linux, and english isn't my mother language. I've found the Gentoo howto weeks ago, but I'm quite afraid of doing a mistake by misunderstandind the howto. I was not sure either it was good for Ubuntu, the conf files are different. This topic fixes things, but a HowTo made specifically for Ubuntu would ease things for us n00bs.

And yes, it's very common on Windows. There's a soft called Notebook Hardware Control that does that, and it's very popular amongs recent notebooks owners : the recent ones often have a problem with temperature. Default voltages are set too high, to prevent freezes on any machine : undervolting the CPU to a self-tailored need reduces the heat without affecting the frequency or performance of the CPU.

---

### Post by ShaLouZa on 2006-04-12
[QUOTE=Jasman]Can you tell me which patch you're referring to? I tried this and the patch and rebuild both bombed out. I have linux-phc-0.2.1-kernel-2.6.15.patch. Thanks.[/QUOTE]
Same here. The phc patch fails 11 hunks and the Bellamy's one found on Gentoo wiki fails 2 hunks. I'm using linux-source-2.6.15, found in Synaptic.

I'd like to see this patch included in the mainstream kernel too. I know what I'm doing when it comes to undervolting, thanks to NHC, but that whole kernel patching thing seems to beat me and I'm afraid to screw up. Looks like I'd have to learn C to rewrite the patch, it's not what I was hoping for. :-k

Besides, it's something that every "advanced" laptop user does on Windows, so the risk is very limited. Someone who doesn't know what to do with undervolting will just not use the function. They will not even notice its existence. And as far as I know, the only risk when you undervolt your CPU is to freeze your system. Then, if someone is stupid enough to over-volt it and fry it... it's natural selection.


edit : I took the 2.6.15.7 source on Kernel.org, patched it with the Bellamy's patch found on the gentoo wiki without warnings or mistakes and... it compiles. :-D 

Bill, we can ship it !

---

### Post by Alor on 2006-04-20
hi. i am one of the authors of [http://linux-phc.sourceforge.net/](http://linux-phc.sourceforge.net/)

if there are any problems with any kernel sources, i would be very interested.

so it would be nice if someone can send me the errormessages while applying the patch and maybe give me a link so that i can download the sources myself. than we will try to change the patch to be compatible with the ubuntu-sources.

a way to use linux-phc without patching is using a kernel-source which already includes the linux-phc patch. at the moment that would be the beyond sources:

[http://iphitus.loudas.com/beyond.php](http://iphitus.loudas.com/beyond.php)


thank you for using linux-phc and for helping to improve it!

roman schwarze

---

### Post by disturbedsaint on 2006-04-26
[QUOTE=klahjn]I'm thinking that it may be kept outside the mainstream, for the simple fact that the n00bs shouldn't be hacking away at this stuff rendering hardware useless by typos or something....or misinformation.  Just a protective measure.  The ones that need that type of patch, probably know already how to compile in support, or are going to research and learn, as i believe it should be.  Not that i would like it difficult for you guys, but i personally would feel more safe if it were more difficult for n00bs to be able to undervolt thier processor to say....something like 3mV or something.[/QUOTE]
As far as I understand it, the stock implementation uses the standard voltages. To undervolt you'll have to change things manually.
So there really isn't anything against implementing it.


[QUOTE=Alor]hi. i am one of the authors of [http://linux-phc.sourceforge.net/](http://linux-phc.sourceforge.net/)

if there are any problems with any kernel sources, i would be very interested.

so it would be nice if someone can send me the errormessages while applying the patch and maybe give me a link so that i can download the sources myself. than we will try to change the patch to be compatible with the ubuntu-sources.

a way to use linux-phc without patching is using a kernel-source which already includes the linux-phc patch. at the moment that would be the beyond sources:

[http://iphitus.loudas.com/beyond.php](http://iphitus.loudas.com/beyond.php)


thank you for using linux-phc and for helping to improve it!

roman schwarze[/QUOTE]
Hi Roman, nice to see you here and pick up a topic related to you work :)

Have you or some else already asked the kernel-developers about impleming PHC?

This should provide you with the possibility to download the kernel-sources:
[http://packages.ubuntu.com/dapper/devel/linux-source-2.6.15](http://packages.ubuntu.com/dapper/devel/linux-source-2.6.15)

As far as using another kernel, since the topicstarter already mentioned that his battery-meter didn't work using the stock kernel.org kernel ([http://www.ubuntuforums.org/showpost.php?p=837951&postcount=5](http://www.ubuntuforums.org/showpost.php?p=837951&postcount=5)) there might be more problems that will surface when using a non-ubuntu kernel.

---

### Post by Egalus on 2006-04-26
The failing of the phc-patch at least had something positive for me:
a) the 0.2.3alpha patch which now correctly reports my pinmodded p-m 
and 
b) longer battery runtimes (versus as vanilla 2.6.15 kernel with phc and same voltages) - at least for my laptop the claim for better powersaving in 2.6.16 seems to be right.

And again thx for this great patch ;)

---

### Post by Alor on 2006-04-26
Hi, thanks for your interest in Linux-PHC!

Ubuntu Forum User bjmg was so nice to change the 0.2.3 version of the patch so that it should work with the 2.6.15 version of the Ubuntu-Kernel.

I have not tested this patch but according to bjmg it should work fine!

[http://www.math.uni-bielefeld.de/~schwarze/linux-phc-0.2.3-kernel-ubuntu-2.6.15.patch](http://www.math.uni-bielefeld.de/~schwarze/linux-phc-0.2.3-kernel-ubuntu-2.6.15.patch)

If you are interested in this, please try out this patch and provide feedback on this forum.

For informations how to apply and use the patch, please visit [http://linux-phc.sourceforge.net/](http://linux-phc.sourceforge.net/)

Thank you,

Roman

---

### Post by bjmg on 2006-04-26
Actually my name is Bernhard J. M. Grün, not Herbert. And I am not an Ubuntu user but I just evaluate it.
Anyway the patch should work as expected.

Bernhard

---

### Post by ShaLouZa on 2006-04-27
Hi, and thanks for your interest in Ubuntu and its users. :-D 

The patch apparently works, I've applied it on the kernel 2.6.15.21.32 source from Synaptic without errors. But I can't check further, my kernel doesn't compile, for some reason. This error doesn't come from the patch, I have it with an untouched kernel too. Here's the log :
> drivers/usb/net/zd1211/zdhw.c:1748: attention : unused variable ‘reg’
  CC [M]  drivers/usb/net/zd1211/zddebug.o
drivers/usb/net/zd1211/zddebug.c: In function ‘zd1205_dump_regs’:
drivers/usb/net/zd1211/zddebug.c:57: attention : unused variable ‘flags’
  CC [M]  drivers/usb/net/zd1211/zdtkipseed.o
  CC [M]  drivers/usb/net/zd1211/zdmic.o
  DEVLIST drivers/usb/net/zd1211/zddevlist.h
make[5]: *** [drivers/usb/net/zd1211/zddevlist.h] Erreur 1
make[4]: *** [drivers/usb/net/zd1211] Erreur 2
make[3]: *** [drivers/usb/net] Erreur 2
make[2]: *** [drivers/usb] Erreur 2
make[1]: *** [drivers] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-source-2.6.15 »
make: *** [stamp-build] Erreur 2
Does that look familiar to someone ? I'm a newbie in kernel compilation, so it doesn't talk to me, and I don't know how to fix it. Did I forget a package, or something ? I've everything that's listed in the depends, recommands and suggests, so I just don't know what to do. :-k

---

### Post by bjmg on 2006-04-27
Hi, this is NOT a problem with my patch!
You have to install gawk to solve that error. Please also delete your /usr/src/linux-... directory to start over.

Bernhard

---

### Post by ShaLouZa on 2006-04-27
[QUOTE=bjmg]Hi, this is NOT a problem with my patch![/QUOTE]
Yup, that's what I said :
> This error doesn't come from the patch, I have it with an untouched kernel too.
As long as the patch huuu... patches, we can assume it's safe. Good work nad thanks again for it. Do you plan to support the following 2.16 version too, or did you explain what you've changed to PHC guys ? I'd sure like to see a PHC patch for Ubuntu all along. 

Thanks for the tip, I'll try that. Well, tomorrow. It's 5 PM here and I already compiled the kernel 4 times today.

---

### Post by Alor on 2006-04-27
Changing the PHC patch to work with some "special" kernel should generally be easy. But someone has to do it and so we are always very thankful for People who do this work.

If you want it in every Ubuntu-Kernel, the best thing to do would be to ask the Ubuntu Kernel maintainers if they like to include it.

Btw:
Is there no "inofficial" Ubuntu-Kernel with new patches and stuff? What do you Ubuntu Guys do if you want to use reiser4 for example?

---

### Post by Egalus on 2006-04-27
We (or at least I) simply download a vanilla kernel and put the patches in we like ;)

Says someone who finally got suspend2 to ram working with inspiron 6000 (which uses sata), yippie ;)

---

### Post by Jasman on 2006-05-05
[quote=ShaLouZa]Hi, and thanks for your interest in Ubuntu and its users. :-D 

The patch apparently works, I've applied it on the kernel 2.6.15.21.32 source from Synaptic without errors. But I can't check further, my kernel doesn't compile, for some reason. This error doesn't come from the patch, I have it with an untouched kernel too. Here's the log :

Does that look familiar to someone ? I'm a newbie in kernel compilation, so it doesn't talk to me, and I don't know how to fix it. Did I forget a package, or something ? I've everything that's listed in the depends, recommands and suggests, so I just don't know what to do. :-k[/quote]

I get exactly the same error compiling in Ubuntu. Only remedy I can figure is to go into the config and uncheck everything having to do with this zd1211 device. Anyone else know about that?

---

### Post by ShaLouZa on 2006-05-05
Did you try that ?
[QUOTE=bjmg]You have to install gawk to solve that error. Please also delete your /usr/src/linux-... directory to start over.[/QUOTE]
I don't have much free time these days, so I don't have yet on my side.

---

### Post by Jasman on 2006-05-07
Bjmg is right that gawk takes care of the compiling error. Thanks. And that updated phc patches cleanly on the latest Dapper kernel. Unfortunately, I then ran into problems compiling my ATI fglrx kernel and my Intel wireless was dead on reboot into the recompiled kernel, so I'm back to square one.

---

### Post by kpolice on 2006-05-07
Yes I have the same problem with my Intel WLAN.

---

### Post by hornett on 2006-05-07
Make sure you have the firmware in the right subdir of /lib/firmware. If you're building from kernel.org, it'll need to be placed directly into /lib/firmware.

Anyway, thanks for the patch, Bjmg! It works a treat for me with the following voltages (on Banias 1.5ghz)

```
1500000:1244,1500000:1244,1500000:1244,1400000:1196,1200000:1100,1000000:1004,800000:908,600000:748
```

---

### Post by Jasman on 2006-05-07
Thanks for the WLAN tip, Hornett. But I got my source through Synaptic, and still lost my WLAN. I guess I need to see what's happening to the firmware after I do it again.

---

### Post by ShaLouZa on 2006-05-08
If you use an Intel 2200 wlan card, take the firmware 2.4 on [ipw2200sourceforge.net](http://ipw2200.sourceforge.net/firmware.php), then copy it to your /lib/firmware directory :

```
#$ tar xfvz ipw2200-fw-2.4.tgz
#$ sudo cp ipw-2.4-* /lib/firmware/2.6.kernel_number
```
It worked for me.

---

### Post by Alor on 2006-05-13
Ubuntu user ballessay changed the gentoo init script so that it works with ubuntu. if you are interested you can download it here:

[http://linux-phc.sourceforge.net/#Download](http://linux-phc.sourceforge.net/#Download)

---

### Post by Jasman on 2006-05-17
i did get the Intel IPW2200 2.4 firmware into /lib/firmware, but then I managed to get my wireless working again with the following commands
```
cd /lib/firmware
sudo ln -s 2.6.15-22-686 `uname -r`
``` 
since I had it running under the latest Ubuntu kernel, which in my case, was 2.6.15-22-686.

I also tried out these init scripts (thanks for the tip, Alor). Now I need to figure out how to trigger those to start at boot.

In order to make it work, I had to copy my exisiting voltage table (gotten with cat /sys/devices/system/cpu/cpu0/cpufreq/voltage_table) and paste it into the /etc/phc-config/undervolt file for both DEFAULT_VTABLE and CUSTOM_VTABLE (the uncommented lines), and then changing only the voltage values in the CUSTOM_VTABLE line. In other words, I needed to duplicate the exisiting list of frequency:voltage pairs, which on my laptop includes 6 repetitions of my 1.86Ghz pair and then 4 lower pairs. I don't know why Ubuntu didn't create the 8 steps my Sonoma should be able to do.

But I still didn't know how to make undervolting start at boot. I was triggering it by doing
```
/etc/init.d
sudo sh undervolt start
``` 
Then I looked back through this thread and found the solution:
```
sudo update-rc.d undervolt defaults
```
Now I get undervolting at boot. Just need to monitor the voltages to see if any are too low (I used those provided in the sample file, which pretty closely match values I've used in NHC in Windows).
Next up is trying to get suspend or hibernate to work!

---

### Post by Jasman on 2006-05-29
Back again. After a reinstall and a couple of kernel recompiles (2.6.16 vanilla with the standard phc patch and now ubuntu 2.6.15-23 with the ubuntu phc patch) I can't get undervolting to work again. When I try to run the undervolt init script for Ubuntu, I get this:

> undervolt: line 61: echo: write error: Invalid argument 
And line 61 in that script (/etc/init.d/undervolt) says

> echo ${1} > ${VTABLE_PATH} && \ 
Finally, VTABLE_PATH is set in /etc/phc-config/undervolt:

> VTABLE_PATH="/sys/devices/system/cpu/cpu0/cpufreq/op_points_table" 
Any ideas why I'm getting this error (I'm way too simpleminded to understand this)?

I just realized my /etc/init.d/undervolt and /etc/phc-config/undervolt files were not set to root ownership, but changing that didn't solve the problem.

Oh, and here's my stupid workaround I just devised (which I don't want to rely on):
In /etc/phc-config/undervolt, I changed the DEFAULT_VTABLE values to equal the CUSTOM_VTABLE values and then in /etc/ init.d issued

> sudo sh undervolt stop

Now, for some reason, stop works, whereas start doesn't. It's now fooled into "reverting" to the undervolted values.

Thanks for any ideas to resolve this.

---

### Post by katzman on 2006-05-30
Hey i am new this the whole kernel thing here....i have tried doing the method you mentioned but after a reboot i can't access any of the sysfs interfaces for the undervolting. Did this actually work for you or was it just an idea?
Also this is the last line in my modules_install
  INSTALL sound/usb/usx2y/snd-usb-usx2y.ko
if [ -r System.map -a -x /sbin/depmod ]; then /sbin/depmod -ae -F System.map  2.6.15.7-ubuntu1; fi

but this is long after the INSTALL....cpufreq...lines so i thought that iw was already installed

edit:
i have gotten rid of that specific error through kernel config and a few similar ones but now have 
  INSTALL sound/pci/hda/snd-hda-intel.ko
if [ -r System.map -a -x /sbin/depmod ]; then /sbin/depmod -ae -F System.map  2.6.15.7-ubuntu1; fi

but i need the intel-hda as that is my soundcard
[QUOTE=quaddy]hi,

i think you dont actually have to compile a whole new kernel.
keeping in mind that the kernel shipped with ubuntu makes use of modules I simply got the kernel-source with apt-get, applied the patch and only recompiled and installed the modules. ( make modules and make modules_install | maybe its prossible to only compile the centrino-speedstep-module but i dont know how, would save some time) 
worked well for me but may lead to problems that i dont have any idea of :)

rebooting after that should do the trick ( reloading the module should also work but the module wouldn't reload because it was in use by other modules )

My personal opinion on including the patch to the shipped kernel is, that it wouldn't be a good idea because you can easily kill your CPU with this and only people who know what they're doing should work with this.[/QUOTE]

---

### Post by Jasman on 2006-05-31
I haven't seen any explanation of getting undervolting to work without a recompile. The recompile isn't bad, and it definitely works, but I'm still having trouble with the init script for some reason (it had worked once before). If anyone has any ideas, it would be appreciated.

---

### Post by katzman on 2006-06-01
I tried the recompile but was havig trouble with nvidia but that is another matter...i oticed though that even though i am using the 2.6.15-23 source it seems to have compiled as 2.6.15-7....odd isn't that :S

---

### Post by Jasman on 2006-06-01
It's not 2.6.15-7, it's 2.6.15.7-ubuntu1....

The ubuntu kernel numbering system is different from the vanilla kernel numbering system, I believe. It's all very confusing.

---

### Post by Jasman on 2006-06-01
It's not 2.6.15-7, it's 2.6.15.7-ubuntu1....

The ubuntu kernel numbering system is different from the vanilla kernel numbering system, I believe. It's all very confusing.

---

### Post by katzman on 2006-06-01
i see.....yes very confusing

---

### Post by bjmg on 2006-06-01
No, it is NOT confusing. It is quite easy.
Let me explain. The last vanilla kernel of the 2.6.15 series is 2.6.15.7 and the Ubuntu developers added some patches tho that vanilla kernel. Therefore they added a "-ubuntu1" to the kernel string.
If they compile an official package they wont use make-kpkg or something like that. Therefore the version number of official ubuntu kernels is different from self compiled kernels.

Easy, isn't it?

---

### Post by Jasman on 2006-06-01
Sorta, but where does the -23 come from and what happened to the .7?

Furthermore, this thread should get back to undervolting. I'm now having trouble compiling modules (well, fglrx) with my current undervolting kernel. That is, I can't compile the module against a custom kernel. There may be a bug involved - I've read something to that effect - but if there is a way to add undervolting to the stock ubuntu kernel without a recompile, obviously we'd all like to know. If anyone knows, please post. Thanks.

---

### Post by 23meg on 2006-06-08
I've applied the patch on the Gentoo wiki to the standard Dapper kernel source on my Pentium M 740 Sonoma (1.73ghz)  and I have quite a weird standard voltage table reported:
```
cat /sys/devices/system/cpu/cpu0/cpufreq/voltage_table
1356,1212,1100,988,4780,4780,4780,4780,4780,4780,4780,4780

```
Shouldn't there be only four values? When I apply the reduced voltages only the first four values change and the undervolting seems to be working, but 4780 is such a high value and I feel it shouldn't be there. What exactly are the rest of the values for?

The author of [this thread]("http://www.ubuntuforums.org/showthread.php?t=97043") seems to have the same CPU as me and they have a different table, with only four values.

Any ideas? Or anyone else with a M 740 running the standard Dapper kernel?

---

### Post by toaste on 2006-06-09
23Meg, if those are voltages in that table, 4.780V will *fry* your processor.  Good thing you can pretty much guarantee the board won't be able to deliver that...

----------------

I run a run a Pentium M 755 and have had a modest, very stable undervolt on Windows for 2 years on my dual-boot laptop.

Now that I've found this tweak, I have some questions about how Linux handles voltage/frequency transitions.  Does this patch basically enable P-State Transitions, so that we must simply modify the voltage table to get an undervolt?  I used RightMark in Windows which enables 7 states by default, but here users are reporting 4 voltages in this table.  Is this configurable, and if so, where can I find the documentation?

----------------

edit: ok, yes this enables P-State Transitions aka "Advanced SpeedStep."  Which means you don't even have to undervolt to see benefit from this patch!

More from Intel: [http://www.intel.com/cd/ids/developer/asmo-na/eng/195910.htm?page=1](http://www.intel.com/cd/ids/developer/asmo-na/eng/195910.htm?page=1)

Take a look at page 4 and you'll see the kernel-resident ondemand govenor is pretty dumb.  When CPU us e is above the high threshold, it throttles wide open.  It then then decreases by steps when CPU use drops below a low threshold.  I'm not sure how bad the userland-to-kernel messaging latency is, but if the userland daemon can be configured for less aggressive throttling, it might be worth it.

---

### Post by 23meg on 2006-06-09
Right.. Here's what I have with the PHC patch against the vanilla 2.6.16.20 kernel:
```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/op_points_table
1730000:1356,1330000:1212,1060000:1100,800000:988,4294967295:4780,4294967295:4780,4294967295:4780,4294967295:4780,4294967295:4780,4294967295:4780,4294967295:4780,4294967295:4780

```I guess only the first four are valid values, right? Safe to ignore the rest?

---

### Post by bartman on 2006-06-09
Hm, I'm using the first 2.6.16 kernel and the voltage table is correct, doesn't show any weird values like yours does.

However you _probably_ don't need to be alarmed by those high values and voltages, as the kernel won't let you set higher voltages than those specified in the speedstep-cenntrino.c source (also stated on the Gentoo wiki page).
For your CPU the following table applies:
```
/* Intel Pentium M processor 740 / 1.73 GHz (Sonoma) */
static struct cpufreq_frequency_table sonoma_1729[] =
{
        OPEX( 798, 133,  988,  988,  988,  988),
        OPEX(1064, 133, 1100, 1093, 1068, 1066),
        OPEX(1330, 133, 1212, 1198, 1148, 1143),
        OPEX(1729, 133, 1356, 1356, 1260, 1260),
        { .frequency = CPUFREQ_TABLE_END }
};
```
columns: frequnecy | fsb | voltage | 3 other interpolated voltages just "for reference" as the author puts it

I have a question myself. Editing the voltage file doesn't work by echoing values to the file (I'm sudoing it naturally). It works, however, if i open the voltage file in a text editor and then save the file. Any ideas on this?
```
$ sudo echo "2133000:1164,1867000:1148,1600000:1100,1333000:1004,1067000:908,800000:700" > /sys/devices/system/cpu/cpu0/cpufreq/op_points_table
bash: /sys/devices/system/cpu/cpu0/cpufreq/op_points_table: Permission denied
```

Another question regarding the scripts for. this. The Linux PHC 0.2.4 changelog says a ubuntu version of the scripts is supplied but my archive only shows the gentoo versions. I'm not that scripting savvy to adapt  them myself (yet) so I'd like to know if anyone has them?

Thanks!

---

### Post by 23meg on 2006-06-09
Things seem to be working for me with these strange values.. Strange. The fan never goes off, but never speeds up either, and even at 100% CPU load with GIMP the processor doesn't heat up. I have yet to do a debug test though.
> 
I have a question myself. Editing the voltage file doesn't work by echoing values to the file (I'm sudoing it naturally). It works, however, if i open the voltage file in a text editor and then save the file. Any ideas on this?Try becoming root with "sudo su" instead.

---

### Post by Alor on 2006-06-11
Hi 23meg,

to say something about the strange voltage values in your /sys/devices/system/cpu/cpu0/cpufreq/voltage_table we need some more infos:

can you please provide the output of
"cat /sys/devices/system/cpu/cpu0/cpufreq/op_points_table"?

And, if you have time, please provide debug info generated by using the phc_debug_report.sh script (with debug info enabled in the kernel).

Please mail all this informations to:

fabrice-bellamy at users.sourceforge.net
rschwarze at users.sourceforge.net

---

### Post by Alor on 2006-06-11
[QUOTE=bartman]

Another question regarding the scripts for. this. The Linux PHC 0.2.4 changelog says a ubuntu version of the scripts is supplied but my archive only shows the gentoo versions. I'm not that scripting savvy to adapt  them myself (yet) so I'd like to know if anyone has them?

Thanks![/QUOTE]

Im very sorry, I think we forgot to include it. There will be a new release soon with the ubuntu-script included.

---

### Post by Jasman on 2006-06-12
The Ubuntu scripts are now included in release 0.25, and I think they were already linked elsewhere on the linux-phc site as of 0.23. I'll have to try them now, since I think I had the wrong script inserted for boot.

Like most of you, I'm getting fewer frequency steps than I do in Windows (a total of 5 versus 8). Don't know if it's possible to edit anything to permit full scaling.

Bartman, since the full script allowing on/off undervolt function wasn't working for me, I've been using this simple undervolting on init script in /etc/init.d

> #! /bin/sh
echo "1084,1084,1084,1084,1084,1084,956,860,764,700" > /sys/devices/system/cpu/cpu0/cpufreq/voltage_table

so it modifies voltage_table rather than op_points_table. This works for me.

I don't know what's up with 23meg's voltage table, unless there's some problem associated with using the Gentoo patch rather than the Ubuntu patch.

Finally, do other folks have any success with using the various governors? I have set up the Gnome CPU Frequency Scaling Monitor to allow me to change the frequencies and/or governors, but the only governor that keeps my CPU at a low frequency is powersave, which basically leaves it at 798MHz. Ondemand, for instance, basically shoots up to 1.86 (I have a 750 Dothan) and stays there. Back in Windows, RMClock or NHC both stay at low frequencies unless I'm doing some intensive processing. In other words, the linux governors seem not to work well. I don't know if this has anything to do with the power daemon being used, but I'm using the default (powernowd). Does anyone use cpufreqd, and does it work differently? Do I have any idea what I'm talking about?!

---

### Post by Alor on 2006-06-12
okay, about the first question:

The number of points you get, is what is provided from your acpi. If you want to change this, you can change your kernel config to "use build in tables". than you can just edit /usr/src/linux/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.c in your kernel source, and add more frequency values at the appropriate place (there is one table for each processor type).
Then you have to recompile your kernel (you should do a "make clean" first) and you will have more op points. If you enter frequencies which are not supported by your kernel, cpufreq will seem to use them, but when you use the "measurefreq" utility provided in the linux-phc tarball, you will see that its not really used.

about your second question:

don't use any graphical tool for more than just for showing the current frequency. use "cpufrequtils" ([http://www.kernel.org/pub/linux/utils/kernel/cpufreq/cpufrequtils.html](http://www.kernel.org/pub/linux/utils/kernel/cpufreq/cpufrequtils.html)) instead.
with "cpufreq-info" it shows you the available frequencies as well as the available governors. You have to activate these governors in you kernel-config! with "cpufreq-set -g conservative" you set it to the conservative governor, which is quite powersaving because it stays at low frequencys as long as possible. on the other hand there is the "ondemand" governor, which stays at the lowest frequency in idle mood as well, but goes directly to the hoghest frequency when the power is used.
if you like, you can use acpid to switch between these governors depeding on if you are on battery or on AC.

I hope this was helpful, put please ask if anything is still not clear to you. i know my english is bad and so my explaations are not very clear.
if it is working for you, please also post a response because it may be helpful for me and for others.

greetz, rschwarze

---

### Post by rabidphage on 2006-06-12
[QUOTE=klahjn]I'm thinking that it may be kept outside the mainstream, for the simple fact that the n00bs shouldn't be hacking away at this stuff rendering hardware useless by typos or something....or misinformation.  Just a protective measure.  The ones that need that type of patch, probably know already how to compile in support, or are going to research and learn, as i believe it should be.  Not that i would like it difficult for you guys, but i personally would feel more safe if it were more difficult for n00bs to be able to undervolt thier processor to say....something like 3mV or something.[/QUOTE]

i didn't have the guts to go for it. well then again curiosity is what we all need. so i just went ahead and compiled the kernal.. in the process did some optimisations as well.. 
so i request you to say something productive and advice me how to configure the votage settings. now i'm running the defaults as in the undervolt file..
BTW this was my first kernel compilation

---

### Post by Jasman on 2006-06-12
If your English isn't clear Alor, then I'm fluent in German! (not)

Really, you are perfectly clear, and thanks for the detailed response. It'll take me a while to digest all of that and figure out my next tweaks. The only thing I'm not sure about is setting the governor with my kernel-config. I assume you mean doing a recompile - correct me if I'm wrong. I remember choosing "userspace" as my default governor, rather than "performance," and I only remember having two choices.

I actually did go ahead and reconfigure my custom compile to use those rectified scripts in PHC 0.25, and it's working fine again.

In order to match my custom voltages to my existing voltages (those provided by acpi, I guess), I issued the cat command for op_points_table and copied the results in the the default line in /etc/phc-config/undervolt, and then just recopied that same line in the custom line, substituting only safe lower voltages for each frequency. Voila, it's working again.

But I will try messing with those governor options at some point, and I'll check out cupfrequtils.

Thanks again.

---

### Post by Alor on 2006-06-14
you're partly right, for the default governor you have to choose between "performance" and "userspace". Here you have to choose userspace to have any chance to change the frequency from userspace.
Directly below this line, you can choose which governors to activate:

  x x <*>   'performance' governor
  x x <*>   'powersave' governor
  x x ---   'userspace' governor for userspace frequency scaling
  x x <*>   'ondemand' cpufreq policy governor
  x x <*>   'conservative' cpufreq governor

I would suggest to activate all of them.
After recompile, you should install "cpufrequtils" if its not yet installed.

Then you should have the commands "cpufreq-info" and "cpufreq-set" and you get the frequency scaling you want :)

@rabidshare: Im not sure I understand your question. are you asking for help with finding the right voltage settings for your processor? I would recommend to use mprime provided by GIMPS ([www.mersenne.org/)](www.mersenne.org/)). The mprime utility has a very good cpu torture test included.
So, when you have mprime, you use cpufreq-set -f 800000 to fix the cpu to a certain frequency. Then you lower the votage for that frequency by using the op_point_table: "echo 800000:900 > /sys/devices/system/cpu/cpu0/cpufreq/op_points_table". Don't go to low at first, otherwise you will crash you computer!
Then you start the cpu torture test provided by mprime. If it runs and it reports no errors, then you can lower the voltage further (in steps of 16mv). So you can just keep the toture test running in one console window and lower the frequency in another window. At some point you will get errors from mprime or yor computer crashes. After that you know, that the last voltage you tried before that was the lowest voltae you can use. To be sure, that this voltage is absolutely safe, you should run mprime at that voltage for at least 6 hours.
Then you continue with the next frequency.
For some hints how low you can go with your voltages: go to  [http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU](http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU) and look at the sample voltages of the other users.

---

### Post by bartman on 2006-06-15
Thanks Alor, I will try it now.

---

### Post by 23meg on 2006-06-15
With the 2.6.16 vanilla kernel patched with 0.2.5 I still have those weird values, plus the values that I echo to the table get interpolated (?) to other values. For example when I do```
$ echo "1730000:1000,1330000:900,1060000:850,800000:800" > /sys/devices/system/cpu/cpu0/cpufreq/op_points_table

```I get```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/op_points_table
1730000:988,1330000:892,1060000:844,800000:796,4294967295:4780,4294967295:4780,4294967295:4780,4294967295:4780,4294967295:4780,4294967295:4780,4294967295:4780,4294967295:4780

```Sorry for not sending debug info; I will as soon as I get round to doing a debug test.

---

### Post by bartman on 2006-06-15
The Ubuntu undervolt script now works like a charm!

After changing the configuration file to fit my CPU I copied both files to their respective places as indicated in the tarball. After that i realised that just having the script in the /etc/init.d folder will do little else than just be there unless I set it up to start at some runlevel. I remembered I the How To about speeding up the boot/shutdown process with sysv-rc-conf and to my amazement undervolt was listed in it's list!

At first I set undervolt to start at runlevel S but I noticed that it reported an error about not finding the voltage_table file. After seeing that ACPI didn't start until runlevel 2 I remembered that this is the time those voltage files are merely created. No wonder the script didn't find them.

So I quickly changed the starting runlevel of undervolt from S to 2, 3, 4, and 5. <read> first sentence of post </read> :)

**Jasman**: There is only one patch, because all distributions use the same kernel
sources.

**23meg**: That works, thanks. But I automated it with the script.
About your problem: try setting all kernel  options under
```
Power management options (ACPI, APM)
   >> CPU Frequency scaling
      >> Intel Enhanced Speedstep
         >> Built-in tables
```
as Alor suggests.

Sorry if my writing seems patronising but writing the basics is a great way of learning for me.


**Alor**, you suggested that setting the cpu governor depending on the source of power can be done via acpid events.

I found events */etc/acpi/events/ac* and */etc/acpi/events/battery*. Can I write a simple script and then add a *action=<path to script>*line to the respecting acpi event?

For instance: I want to lock the cpu to the lowest frequency when using the battery, so I write a litle script: ```
#!/bin/sh
# Sets the powersave CPU governor which locks the CPU to it's lowest multiplier 

cpufreq-selector -g powersave
``` and add a line to */etc/acpi/events/battery*:
```
# /etc/acpi/events/battery
# Called when AC power goes away and we switch to battery

event=battery
action=/etc/acpi/power.sh
#THIS IS  THE ADDED LINE:
action=/etc/acpi/powersaving.sh

```

Will this work? I'm particularly having doubts about two [i]action=[/] lines in the acpi event file.


Thank you for your comments.

---

### Post by Alor on 2006-06-15
@bartman:

I dont know nothing about how acpi is handled in ubuntu. But what you have done is worth a try I think :)

If it is not working with two "action" lines, you can probably just add your script to the "/etc/acpi/power.sh" script.

Im glad, linux-phc is finally working so well for you!

@23meg:

the voltages are rounded to multiple of 16mv. thats totally normal. your strange voltages are a result of strange data comming from the bios (the acpi). But if ou provide us with some debug info, we may be able to change our patch, so that it does a better checking on the values coming rom the bios.

Thank you all for your feedback!

---

### Post by Jasman on 2006-06-16
[quote=Alor]
  x x <*>   'performance' governor
  x x <*>   'powersave' governor
  x x ---   'userspace' governor for userspace frequency scaling
  x x <*>   'ondemand' cpufreq policy governor
  x x <*>   'conservative' cpufreq governor

I would suggest to activate all of them.
After recompile, you should install "cpufrequtils" if its not yet installed.

Then you should have the commands "cpufreq-info" and "cpufreq-set" and you get the frequency scaling you want :)[/quote]
Thanks, Alor

So, I recompiled, this time unchecking the "get info from ACPI" (or whatever it is) option (I also unchecked Banias and Dothan tables, since this is "Sonoma" (aka, 133 FSB). Then I edited speedstep_centrino.c to add in intermediate pairings, making a total of 8. Finally, I edited the init script to include 8 steps at both standard voltages and undervolted numbers for custom. And then I installed cpufrequtils.

Good news, the 8 steps are working with undervolting!

Not so good - even when setting the governor to conservative, the cpu's frequency shoots up to 1.86 pretty quickly and then stays there. This doesn't seem "conservative" to me. The only thing I can think of is that in my scripts, I left both default and custom op_points_tables with 11 pairings, as it was when I had the pairings determined from ACPI. Before, the first 6 pairings were the top frequency (1.86), and now only the first 3 pairings are 1.86, since I added in 3 new intermediate pairings.

Maybe I should delete all but one of the 1.86 pairings? Or is there something about the way these governors work that I should understand better.

I can, of course, set userspace governor and select my frequency or powersave and it will go to 796. But it'd be nicer to have automatic speedstep operation, and then maybe vary it with acpid for customized operation on battery or when plugged in.

Thanks again.

---

### Post by bartman on 2006-06-17
Two *action=* lines in acpi events don't work. So editing power.sh is probably the best option.

Jasman: If you use powernowd, you can set how it handles load and frequency scaling. See thread [Custom powernowd Parameters](http://ubuntuforums.org/showthread.php?t=19146), more specifically the first 4 posts and then read *man powernowd* for setting the right mode (-m 2 means passive mode, which gradually increases the frequency under load but sets the lowest frequency when there is little load).

This is starting to be offtopic but I'd like to know what you use for frequency scaling - powernowd or cpufreqd?

---

### Post by Alor on 2006-06-17
Jasman,

is it by any chance possible that you are using more than one pogram which tries to change the frequency of the cpu?

and, if you don't start the script at bootup and use standard voltages, is cpufreq working correctly then?

when you enable debug info, like explained in the README, you can see in dmesg what program is changing the fequency.

Oh, and by the way: you are sure your computer is idle, right? its not the case that some program is using so much cpu that cpufreqd is not lowering the frequency?

---

### Post by Jasman on 2006-06-18
After a little downtime with a failed attempt at installing a new splash screen for my custom PHC kernel, I corrupted my root ext3 filesystem and had to reinstall (why is ext3 so easy to corrupt?). Now I'm back and I am noticing that my stock install seems to throttle down a little more on the CPU - although not nearly as much as I'm used to in Windows (the default in Windows seems to be lower frequencies, not higher).

So maybe I did have more than one program trying to change the frequency, but I'm not sure how I'd figure this out. Maybe I installed cpufreqd and it was competing with powernowd, or something like that. I can't recall.

I'll be trying a new recompile, and this time I'm going to try to limit the frequency/voltage pairs to eight in the config scripts and see what happens.

BTW, I wouldn't be complaining about this if I was running lots of memory-intensive programs. I was experiencing full-throttle with no programs open. However, I was easily able to throttle down with userspace control to the lowest frequency, or any one in between, and stay there as long as I wanted.

---

### Post by Jasman on 2006-06-19
[quote=bartman]See thread [Custom powernowd Parameters]("http://ubuntuforums.org/showthread.php?t=19146"), more specifically the first 4 posts and then read *man powernowd* for setting the right mode (-m 2 means passive mode, which gradually increases the frequency under load but sets the lowest frequency when there is little load).[/quote]

Bartman, I hadn't read your message, sorry. Thanks for the tip, since that really addressed the problem. So, at this point, I'm just using powernowd with this custom setting, as in the above mentioned thread, and the dafault frequency is now clearly at the low end, rather than the high end.

---

### Post by Alor on 2006-06-19
good to know that it's finally working for you :)

for me, with gentoo, cpufreqd was always the most easiest solution but maybe with ubuntu it is different.

greetz, rschwarze

---

### Post by Jasman on 2006-06-20
Alor, can you explain what you see as the difference between powernowd and cpufreqd, because I still find that even with the custom powernowd parameters, the frequency scaling seems a little erratic - or it just seems to hang too long at some frequencies. I might try cpufreqd to see if there's any difference. Thanks.

---

### Post by Alor on 2006-06-20
actually, I just discovered that I'm not really using cpufreqd. I'm just using the cpufreq provided by the kernel together with cpufreq-set from the cpufrequtils package.

That means, I'm not starting any service to control the frequency, I'm just using "cpufreq-set" to choose the governor at startup.

---

### Post by Jasman on 2006-06-20
Well, but the default install is powernowd, not cpufreqd. Are you sure you aren't running powernowd?

---

### Post by Alor on 2006-06-21
yes, pretty sure :)

I'm not running ubuntu also by the way, so there should be no default install ;)

---

### Post by Sencer on 2006-06-22
This is great! A great topic and a lot of useful tips. Though I do hope this will eventually make it into ubuntu/kernel.

I have a Sonoma 740 (Pentium M 1.73, FSB533) and my notebook has been running mprime successfully with 
```
1733000:1116,1333000:940,1067000:860,800000:748
```
for a while now, though I am still in the process of stress-testing. My temperture dropped by ~5°C [at 800Mhz) which makes just the difference between the fan running under load, and not running. 8) 

I started out with the values other people got (on the gentoo-page) with the 740  cpu - but got erors rather quickly - I think the examples given there are a little bit optimistic and tend to show more of those people lucky enough to get real low. Then again, I just may be a little bit unlucky. ;)


Given that I have little knowledge to add to this topic, I'll try to summarize the things from here and other topics that helped me:

1) Simple Kernel Compile howto:
[http://www.ubuntuforums.org/showthread.php?t=43065](http://www.ubuntuforums.org/showthread.php?t=43065)

2) I stuck with the ubuntu-sources (**linux-source-2.6.15**, version shows 2.6.15-25.43, i.e., most recent) which got me a uname of 2.6.15.7-ubuntu1... which is equivalent to the most recent official ubuntu binary kernel. (got confused with those numbers at first as well :mrgreen: )

3) I had to install the **gawk** package, otherwise the compile stops halfway through. I also had to use the **--initrd** for **make-dpkg** otherwise I couldn't boot with the new kernel (IIRC: Kernel panic - not syncing: VFS: Unable to mount root fs ... )

4) I had to follow Jasman's tip to keep my ipw2200 working, which was
```

cd /lib/firmware
sudo ln -s 2.6.15-25-686 `uname -r`

```

5) When this happened:
```

sudo echo "2133000:1164,1867000:1148,1600000:1100,1333000:1004,1067000:908,800000:700" > /sys/devices/system/cpu/cpu0/cpufreq/op_points_table
bash: /sys/devices/system/cpu/cpu0/cpufreq/op_points_table: Permission denied

```
I solved it by dropping to a root shell:
```

sudo su
echo "2133000:1164,1867000:1148,1600000:1100,1333000:1004,1067000:908,800000:700" > /sys/devices/system/cpu/cpu0/cpufreq/op_points_table

```

6) Then I started following Alor's instructions from [Post 58 on page 6](http://ubuntuforums.org/showpost.php?p=1136164&postcount=58) and [gentoo's undervolting page](http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU), which show how to find values that work for a specific machine. 


Thank you everybody in this thread. Your help, kindness and suggestions were great. (It was what made me register now). Ok, I have to go find some more Mersenne prime numbers now... ;-)

---

### Post by Alor on 2006-06-23
Hi Sencer!

Good to hear that you got everything working. :)

Thank you very much for this nice Howto, I think it will be helpful for lots of other ubuntu users and it covers all the things I cannot help with cause I never used ubuntu.

greetz, Roman

---

### Post by bartman on 2006-06-26
I found a better way to execute scripts on power source change. In /etc/acpi/power.sh there are a few lines which  execute all *.sh scripts in /etc/acpi/ac.d and /etc/acpi/battery.d, depending on the power source.

So i placed my one-line scripts into those folders and I'm definitely a happier camper! ;)

---

### Post by ariel on 2006-06-27
Quick question... does the undervolting patch support Yonah (Core Duo, low voltage version)? I have an X60s that runs much (very much) colder in Windows than Ubuntu, and I am getting a much (very much) shorter battery life (about 40% less time with Ubuntu than with Win).

Has someone tried this in a Yonah machine?

Thanks!!

---

### Post by bartman on 2006-06-28
I'm not exactly sure, but I think it should work if you DO NOT use the built-in tables kernel option.

You might find that these tables are actually not yet built-in into the patch so i think the voltages have to be read from the CPU. :confused: 

Then the kernel should generate apropriate files in /proc which you can change.

But we should probably wait for Alor's explanation.

---

### Post by alto123 on 2006-06-28
I am a Linux newbie and I would be very glad to have PHC running - but the stuff in this thread is a bit too much for me :( Would it possible for you to post a simple step-by-step howto, for Ubuntu Dapper Drake (6.06) that would explain:

1. What packages to download via Synaptic (kernel-source, gcc, what else)
2. How to patch (ok, this is explained in PHC readme, but for completeness)
3. How to configure the kernel (ok, make menuconfig - but what options to select to end up with the kernel configured exactly like my current kernel - PHC exluding of course).
4. How to compile it & install in GRUB :-)
5. Post it on Ubuntu Wiki perhaps?

I guess it would make life much easier for all us, Windows converts :-)

Many thanks in advance!!!

---

### Post by alto123 on 2006-06-29
[QUOTE=alto123]I am a Linux newbie and I would be very glad to have PHC running - but the stuff in this thread is a bit too much for me :( Would it possible for you to post a simple step-by-step howto, for Ubuntu Dapper Drake (6.06) that would explain:

1. What packages to download via Synaptic (kernel-source, gcc, what else)
2. How to patch (ok, this is explained in PHC readme, but for completeness)
3. How to configure the kernel (ok, make menuconfig - but what options to select to end up with the kernel configured exactly like my current kernel - PHC exluding of course).
4. How to compile it & install in GRUB :-)
5. Post it on Ubuntu Wiki perhaps?

I guess it would make life much easier for all us, Windows converts :-)

Many thanks in advance!!![/QUOTE]


Just for completeness - I have a Atheros Wifi card and it seems to be giving lots of problems. I kinda managed to compile the kernel and got PHC running (I think so) but my WiFi and Ubuntu splash stopped working. I guess that for WiFi I have to build also "restricted" modules - but I cannot find the source in Ubuntu repositories (in Synaptic) - with all repositories switched on I can find only binary packages for restricted modules.

Help anyone? Please??? :-)

---

### Post by shu on 2006-07-01
Guys, I've followed your guide and managed to undervolt my laptop or at least I think so. I have few questions tough. In my op_points_table there are 10 pairs, but the first 7 are the highest frequency. Am I free to change them to something else to get better scaling?

Also is there a way to check what voltage is cpu currently using? I found a script on gentoo wiki  that is supposed to do just that, but it reports 0mV all the time.

---

### Post by Alor on 2006-07-01
@ ariel: there are people who tried the patch on a core duo, and it should work somehow. these people have posted on  [http://forums.gentoo.org/viewtopic-t-341298-postdays-0-postorder-asc-start-225.html?sid=b5d1b9b5f38611a5343bb8df7b2bdaa1](http://forums.gentoo.org/viewtopic-t-341298-postdays-0-postorder-asc-start-225.html?sid=b5d1b9b5f38611a5343bb8df7b2bdaa1)
please read there posts. i don't have a core duo myself, so i cannot say anything myself. but you can at least try, and look what the op_points_table looks like.
Please report your experience on this thread, so we can try to improve linux-phc for core duo!

@shu: only the last one of the highest frequencies should have an effect.
there is no way, to directly grep the frequency which is currently used. but the voltages in op_points_table should be appropriate.

@ alto123: I don't have ubuntu and I don't have an atheros card myself. Maybe you should go to the sourceforge page of the atheros driver and follow the install manual there. that means, install the driver manually instead of using synaptic.

---

### Post by shu on 2006-07-01
Hm, guys is it possible to have more than 4 steps? I only get 800, 1060, 1330 and 1730 MHz volatages, but there are 10 entries in the table. Is it possible to have more fine grained steps? Does it even make sense?

---

### Post by 23meg on 2006-07-06
After various attempts with a vanilla kernel, I decided to try to recompile the Dapper kernel from the source in the repos with the Ubuntu patch from PHC 0.2.5 and here's what happened:

I echoed the following (quite conservative) voltage values for the four steps of my 1.73ghz Sonoma (740): 850, 900, 980, 1050 , which had worked fine before with the vanilla kernels. I tried all speed steps one by one, to see if I'd get a crash (I did get crashes with too low values with vanilla kernels); with the lowest three steps everything was fine, but at the fourth and highest speed of 1.73ghz the screen immediately went blank.

I shut down the computer with the power button, attempted to start again, but it wouldn't start; the power light comes on for half a second, the HD tries to spin up, but everything shuts down again within a second. Probably my CPU was damaged, and this won't be covered by warranty.

My kernel config was as suggested in the PHC documentation.

I'm taking my laptop to a service center now; I'll report back on what exactly was damaged.

EDIT: The service center reported today that the mainboard was damaged.

---

### Post by Alor on 2006-07-12
Hi 23meg!

i'm very sorry for your loss!
i hope, the warranty covers your defect mainboard, i think it should. i have actually no idea what might have happen to your mainboard.

greetz,

roman

---

### Post by 23meg on 2006-07-13
Fortunately it looks like it will be covered by warranty, unless a last minute glitch arises. In any case I've lost my only computer for at least 20 days in a busy work period and have of course lost all willingless to experiment any further with undervolting.

---

### Post by ariel on 2006-07-16
> **23meg said:**
> Fortunately it looks like it will be covered by warranty, unless a last minute glitch arises. In any case I've lost my only computer for at least 20 days in a busy work period and have of course lost all willingless to experiment any further with undervolting.

Happy to hear that!  Can you mention what is your laptop make & model?

---

### Post by 23meg on 2006-07-16
Toshiba Tecra M4, with a 1.73ghz Pentium M (740, Sonoma chipset).

---

### Post by Alor on 2006-07-22
Hi all!

There is a new release of Linux-PHC, version 0.2.6.
The most important changes are a new safety code to avoid using invalid operating points on some laptops and support for the new ubuntu kernel, 2.6.17-5.15.

You can read the complete changelog as well as download the new version from [https://www.dedigentoo.org/trac/linux-phc/](https://www.dedigentoo.org/trac/linux-phc/)

greetz, rschwarze

---

### Post by 23meg on 2006-08-10
Alor: do you have any idea what may have gone so wrong in my case? Do you think it can be related to FSB speed being incorrectly reported? I should stress again: my motherboard was said to be damaged, not the CPU, and everything worked fine with a vanilla kernel.

---

### Post by brambi on 2006-10-20
I wrote a small howto, on how to get undervolting working on Ubuntu Edgy:
[https://wiki.ubuntu.com/UndervoltingHowto](https://wiki.ubuntu.com/UndervoltingHowto)

Bram.

---

### Post by Kateikyoushi on 2006-10-20
That's good thanks, the only thing which held me back from undervolting my edgy system was the wekkly new kernel if it slows down I do it.

---

### Post by Sencer on 2006-10-28
Quick note: Since ubuntu edgy uses dash as sh ([https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)) the init-scripts in the linux-phc 0.2.7 are "broken". You'll get the message:
```
./undervolt: 14: source: not found
```

The fix is trivial though, simply replace the shebang in etc/init.d/undervolt from #!/bin/sh to #!/bin/bash

Alternatively change "source" in line 14 with "." as per [https://launchpad.net/distros/ubuntu/+source/dash/+bug/65046](https://launchpad.net/distros/ubuntu/+source/dash/+bug/65046). Tried that as well, and it seemed to work ok.

---

### Post by extremecarver on 2006-10-28
Help: Can anybody explain me how to get rid of those messages?
Kernel 2.6.17 from Kernel.org and Beyond4 = 2.6.17.13 or so.



```
  GEN     .version
  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
init/built-in.o: In function `try_name':
do_mounts.c:(.text+0x604): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
(.text+0x909): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
(.init.text+0xbd3): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
initramfs.c:(.init.text+0x1924): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o: In function `arch_ptrace':
(.text+0x5281): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:intel_cacheinfo.c:(.text+0x9e43): more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.17'
make: *** [debian/stamp-build-kernel] Error 2
root@felix-laptop:/usr/src/linux# 
```

---

### Post by extremecarver on 2006-10-28
ups Sorry, got this in the wrong thread - but of course my aim is to undervolt. I did do quite a lot succesfull kernel builts with dapper. With edgy I constantly run into errors ](*,) 
Will post it at the end of kernel compile howto too.

---

### Post by extremecarver on 2006-11-02
Please help me getting it to autostart. I can undervolt and I did everything as told in the undervoltinghowto (well everything after the kernel part, as I compiled a beyond2.6.17.13 beyond4 kernel)

I changed etc/init.d/undervolt to bin/bash
I entered the voltages into Custom V-Table. and setting it to yes
I entered the startup script exactly as written here with this command  "cd /etc/rc2.d/
sudo ln -s ../init.d/undervolt S95undervolt"

However oopointtable does not get updated after reebot!
Any solutions - manually setting oopointstable works as I can see temperature decreasing on my 735 modded to 780 by 10 Degrees Celsius and the file voltage table then afterwards updating itself.

Help for any input (oh system is Edgy Eft)

---

### Post by extremecarver on 2006-11-02
Works now - I needed to uninstall CPUFREQ ](*,)
It actually completely disabled my undervolt. Don't know whats wrong with it? Reinstalled and same problem again. Uninstalled and undervolt works.
(with cpufreq installed I can't even access the ooppointstable anymore. 

Anyone knows a daemon to allow me changing that works with the undervolt script under egdy? Under dapper undervolt script and CPUFreq worked fine together.

Powernowd doesn't allow me changing the frequency.

---

### Post by brambi on 2006-11-03
> **extremecarver said:**
> 
Anyone knows a daemon to allow me changing that works with the undervolt script under egdy? Under dapper undervolt script and CPUFreq worked fine together.



Hi the build-in (kernel) scaling governor is improved in the kernel in edgy and I use that one. It should be enabled automatically. You can check it if you cat a file in the sys directory:

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

You should see 'ondemand'. That's probably the governor 95% the people want. 
It works just fine in combination with my undervolting howto :) (considering you didn't undervolt your system too much).

---

### Post by brambi on 2006-11-03
> **Sencer said:**
> Quick note: Since ubuntu edgy uses dash as sh ([https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)) the init-scripts in the linux-phc 0.2.7 are "broken". You'll get the message:
```
./undervolt: 14: source: not found
```


The author of the linux-phc fixed that. The patch will be in the next release.

---

### Post by vmalep on 2006-12-06
My provider advised me to have a look at this page: [http://developer.intel.com/design/mobile/pentiumm/documentation.htm](http://developer.intel.com/design/mobile/pentiumm/documentation.htm) where we can find technical data, incl. re. the voltage definition for the Pentium M (by following the links in Datasheets and looking in the pdf files available). But I am not sure how to apply these details...

---

### Post by Jasman on 2006-12-17
Hi. Just thought everyone on this thread should know to look at at bug report on launchpad, here: [https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.20/+bug/63789](https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.20/+bug/63789)
Near the bottom you'll find links to actual patches that can be applied to the Edgy and (2.6.19) Feisty kernels - no kernel recompile necessary. The debs even add the appropriate boot scripts. If you install on Edgy, you might need to modify the /etc/init.d/undervolt script as detailed earlier in this forum thread ("/bin/bash" instead of "/bin/sh" and ". $CONFIGURATION"), since the patch for the 2.6.17 kernel is linux-phc 0.2.7, and only 0.2.8 has corrected these details.

I just did this with the 2.6.17 kernel and it worked like a charm. I then installed stock ATI drivers, also no problem. For anyone with headaches after trying to compile your own kernel, this is the way to go.

---

### Post by ballessay on 2006-12-18
Hi.
I have recently installed Edgy and tried out the package for linux-image-2.6.17-10-generic
> **Jasman said:**
> [https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.20/+bug/63789](https://bugs.launchpad.net/distros/ubuntu/+source/linux-source-2.6.20/+bug/63789)

and it works very fine for me. :D 
> **Jasman said:**
> 
If you install on Edgy, you might need to modify the /etc/init.d/undervolt script as detailed earlier in this forum thread ("/bin/bash" instead of "/bin/sh" and ". $CONFIGURATION"), since the patch for the 2.6.17 kernel is linux-phc 0.2.7, and only 0.2.8 has corrected these details.
.
But in the deb i've downloaded the ". $CONFIGURATION"-change was made so there is no need to edit anything like the shebang. ;) 
In dapper the old script worked very well :-k 

greetings
ballessay

---

### Post by Jasman on 2006-12-19
> **ballessay said:**
> 
But in the deb i've downloaded the ". $CONFIGURATION"-change was made so there is no need to edit anything like the shebang. ;) 
In dapper the old script worked very well :-k 


I had already edited my script for a previous attempt at installing with a recompiled kernel. I think the deb corrected something I missed in setting it up for all the user levels (I had previously just followed others' directions, which had worked for me a while ago). Anyway, long story short, I couldn't get both undervolting and my graphics driver installed perfectly until I found these debs, so I vote for continuing to update these packages in the Ubuntu repos. Thanks for the nice work, Phillip Dreimann.

---

### Post by Wall86 on 2006-12-19
my dell latitude c400, currently has the opposite thing going on, it is a 866 Mhz, but it uusually runs at 156 Mhz, and it gets bloody hot, like i am talking hotter then a p4 OC'ed with no heatsink hot..... This is a windows maxchine right now (working on doing a net install in the near future) but any ides on fixing this?

---

### Post by Jasman on 2007-01-14
No one's replied to this last post, but I'll just say that I don't think the question really belongs here. Undervolting is different than the actual control of CPU operating frequencies, even though that's been an issue for a lot of us trying to undervolt. Can anyone comment about basic problems with CPU frequency scaling?

---

### Post by tawk on 2007-01-18
@Undervolters
As spoilerhead from ubuntuusers.de found out, there is a much more easy way to undervolt your CPU. Just compile the single module and replace it in the running kernel. No endless kernel-compiling and problems afterwards.

First, extract your kernel-sources and patch them with linux-phc. After configuring with existing ".config" and "make oldconfig" you can go on here:
```
make prepare
make scripts
make M=./arch/i386/kernel/cpu/cpufreq
```

Now you will find the module "speedstep-centrino.ko" in "arch/i386/kernel/cpu/cpufreq". This file is all you need.
For copying the module to the running kernel you will need root-access. 
Please make a backup of your old module, in case there goes something wrong!
```
sudo cp speedstep-centrino.ko /lib/modules/$(uname -r)/kernel/arch/i386/kernel/cpu/cpufreq
```

Reboot and have fun!

I wrote an [entire HOWTO]("http://wiki.ubuntuusers.de/Prozessorspannung_absenken") about that, but it's in german. I hope someone can figure out what I meant with this post ;-)

---

### Post by use R on 2007-01-22
Hello, 
@tawk,
I have seen the above mentioned howto ([http://wiki.ubuntuusers.de/Prozessorspannung_absenken)](http://wiki.ubuntuusers.de/Prozessorspannung_absenken)), it's great. It works fine until I come to the following problem:
after patching and so on, I want to look at the voltage table with: 
[cat /sys/devices/system/cpu/cpu0/cpufreq/op_points_table]
but the folder is completely empty. Why is this file missing, where can it be?
I used the the same versions of patch and source that are specified in the howto.
I am using Ubuntu Dapper 6.06 LTS. Let me know what additional info you need.
Any help would be very much appreciated!

---

### Post by Jasman on 2007-01-26
Thanks, Tawk. I'm giving this a try. Just out of curiosity, what's the Kconfig file for, and why doesn't it matter in this process? It's the other file that's patched by Linux-PHC. Also, is there anyone who can translate that entire HOWTO from German to English? Maybe I'll feed it through a translator and see what I come up with. Thanks again.

---

### Post by tawk on 2007-01-27
The Kconfig file is needed for the configure Process (make oldconfig) where you are asked whether you want to enable built-in tables and so on.

If you don't want to compile the module, you can take the one in the attachment for a edgy stock kernel. 
After extracting, just copy it to the running kernel. But please make a backup of your old module!
```
sudo cp speedstep-centrino.ko /lib/modules/$(uname -r)/kernel/arch/i386/kernel/cpu/cpufreq
```
Reboot, [and try using the patch]("https://www.dedigentoo.org/trac/linux-phc/wiki/UsingTheSysFsInterface")

---

### Post by damiencc on 2007-02-01
Many many thanks, one kernel compilation avoided !

---

### Post by D-- on 2007-02-03
Has anyone had any luck doing this on feisty? I did the feisty upgrade last night and was a bit bummed to see it's up to kernel 2.6.20-6. The PHC website says the SVN of 0.2.9 has support for this kernel, but it's only the vanialla kernel so it doesn't really patch onto ubuntu. I've tried the old tutorial (no luck) and tawk's post (compiles everything EXCEPT centrino beause the 2.6.20 patch really isn't appropriate for ubuntu's kernel).

Would kill for a deb file if anyone has gotten this to work on the current feisty,

---

### Post by spoilerhead on 2007-04-21
*casts ressurect*

feisty version of the PHC patch (click [phc_feisty.tar.gz]("http://stud3.tuwien.ac.at/~e0326004/linux/phc_feisty.tar.gz")) includes patched Makefile, Kconfig and speedstep-centrino.c, and a precompiled speedstep-centrino.ko module for feisty kernel.

sorry, i had no time to create a .patch file, so if someone could create it it would be cool ;)

---

### Post by annotei on 2007-04-21
thanks a lot, it works :)
It's not user-friendly but for those who can't wait it's excellent :)

Antoine.

---

### Post by spoilerhead on 2007-04-21
finally i had some time to create a .patch file

get it here: [Download]("http://stud3.tuwien.ac.at/~e0326004/linux/linux-phc-0.2.9-kernel-ubuntu-2.6.20_sph.patch")

edit, updated the patch as i screwed up the previous version ;)

---

### Post by extremecarver on 2007-04-25
Could you please explain how to apply the patch?

Should I download 2.6.20-xx from ubuntu and then apply the patch and compile it?
Do I need the patch or is speedstep centrino.ko enough?

---

### Post by jimmyp on 2007-04-25
Thanks for the informative thread guys.

My acer travelmate 4652 lmi (sonoma 740 M 1.73ghz cpu) has a battery life of about 4 hours in windows xp and the fan hardly ever runs.  In linux, however, the battery life is 2.5 hours and the fan is always on.

Last night I used spoilerhead's speedstep-centrino module to undervolt.  I got my lowest frequency, 798 mhz to run at 700mV without primes crashing or reporting an error overnight.  However, even at that frequency, with 700mV, the fan is still always on, and the battery life is not increased. :-k  What's the deal?  What else should I do to make the fan behave as it does in windows?

Also, my default volt table, according to op_points_table, reported that 798mhz had a voltage of 988.  Does this number come from the bios?  Does windows use this number?  If so, how can it shut the fan off if it runs so hot?  If not, where does windows get its voltages from?

Thanks for the help.

@extremecarver I am fairly certain that spoilerhead's speedstep-centrino.ko is enough.  But since you are using the module, you can't pass cpufreq.debug=3 or whatever number you want to use when you boot, you have to specify that option somewhere in /etc.  /etc/modprobe.d/options I believe.

---

### Post by extremecarver on 2007-04-25
> **jimmyp said:**
> Thanks for the informative thread guys.

My acer travelmate 4652 lmi (sonoma 740 M 1.73ghz cpu) has a battery life of about 4 hours in windows xp and the fan hardly ever runs.  In linux, however, the battery life is 2.5 hours and the fan is always on.

Last night I used spoilerhead's speedstep-centrino module to undervolt.  I got my lowest frequency, 798 mhz to run at 700mV without primes crashing or reporting an error overnight.  However, even at that frequency, with 700mV, the fan is still always on, and the battery life is not increased. :-k  What's the deal?  What else should I do to make the fan behave as it does in windows?

Also, my default volt table, according to op_points_table, reported that 798mhz had a voltage of 988.  Does this number come from the bios?  Does windows use this number?  If so, how can it shut the fan off if it runs so hot?  If not, where does windows get its voltages from?

Thanks for the help.

@extremecarver I am fairly certain that spoilerhead's speedstep-centrino.ko is enough.  But since you are using the module, you can't pass cpufreq.debug=3 or whatever number you want to use when you boot, you have to specify that option somewhere in /etc.  /etc/modprobe.d/options I believe.

1. To my experience whatever is written in oopointstable is correct. So if there is written 998 you are on 998 and not on 700. Just write in a very low voltage for high frequency and see if it crashes. If yes bingo the voltages work and start up a recovery kernel that does not support the change in voltages to reset everything.

2. I don't know what you mean with cpufreq debug=3. I'ld really need a step by step explication. 
I did implement the .ko (without patch) only and now I have under sys/devices..... cpufreq - all files are existing but not oopoints as I was used too. Where's the catch?

---

### Post by spoilerhead on 2007-04-25
the speedstep-centrino.ko file is enough, just replace the one in your modules directory with it

to use the patch, you need the linux-source packed from feisty, apply it and then compile it
the only difference to the default kernel is the also posted speedstep-centrino.ko file, so the patch ist just there for completeness (or if you want to build a custom kernel)

---

### Post by extremecarver on 2007-04-25
So have you got any idea why I then can't find the oopointstable??
Without the modified centrino ... .ko I can't acces cpufreq at all (it only shows topology).

Can I just setup the init scripts without an existing oopointstable?

---

### Post by jimmyp on 2007-04-25
> **extremecarver said:**
> 1. To my experience whatever is written in oopointstable is correct. So if there is written 998 you are on 998 and not on 700. Just write in a very low voltage for high frequency and see if it crashes. If yes bingo the voltages work and start up a recovery kernel that does not support the change in voltages to reset everything.

Yes, sorry, I meant before I fiddled with the voltage table it said 988.  I lowered it down to 700 and didn't have a crash.  But it didn't seem to affect my battery life or fan, even when I only run at the lowest frequency, which uses 700mV.  I know that my changes are having some effect because when I lowered the voltage for higher frequencies and ran primes at the higher frequencies my machine crashed.

> **extremecarver said:**
> 
2. I don't know what you mean with cpufreq debug=3. I'ld really need a step by step explication. 
I did implement the .ko (without patch) only and now I have under sys/devices..... cpufreq - all files are existing but not oopoints as I was used too. Where's the catch?

You have to reboot after you copy the modified module over the old one.  Or at least remove the old speedstep-centrino module and insert the new one.

---

### Post by spoilerhead on 2007-04-26
> **extremecarver said:**
> So have you got any idea why I then can't find the oopointstable??
Without the modified centrino ... .ko I can't acces cpufreq at all (it only shows topology).

Can I just setup the init scripts without an existing oopointstable?

no, you need he ooppointtable.

did you reload the module / reboot your pc?

if yes, maybe ask at[ the phc homepace]("https://www.dedigentoo.org/trac/linux-phc/")
but it seems that it still has some problems  with core 2 duos

---

### Post by extremecarver on 2007-04-26
I rebooted several times, tried inserting it into the active kernel just running, or tried to insert it into another kernel not actually loaded and then rebooting into that one. Tried it with sudo and tried it with root user access. All to no avail. I know that the knew centrino.ko is in there because without it I have no cpufreq but it hasn't got the oopointstable.

I've got a Pentium M Dothan pinmodded to Sonoma which worked with a beyond 2.17 kernel and Dapper Drake. Seems to be some other sort of problem. Kernel version is 2.6.20-15.27 386 or generic. Low-latency doesn't work at all.

---

### Post by spoilerhead on 2007-04-26
try unloading it, then reload it and then give us the output of a 
dmesg |tail -n30

maybe its also a bug somewhere and you should report it to the linux-phc homepage

---

### Post by extremecarver on 2007-04-26
How to unload it? 
I'm a linux noob - I can only do whatever I see in direct quotes to copy into terminal.

I'll go and search but that might take some time.

I think I allready had a similar problem on this computer so maybe really there is something broken but it worked in dapper. I think I never got it to work in egdy either.In windows neither NCC not RMClock makes probs though.

Here is the output without unloading or loading something special:
> [   21.052000] No dock devices found.
[   21.080000] ibm_acpi: ec object not found
[   21.128000] input: Lid Switch as /class/input/input7
[   21.132000] ACPI: Lid Switch [LID]
[   21.156000] input: Power Button (CM) as /class/input/input8
[   21.160000] ACPI: Power Button (CM) [PBTN]
[   21.184000] input: Sleep Button (CM) as /class/input/input9
[   21.188000] ACPI: Sleep Button (CM) [SBTN]
[   21.484000] ACPI: Battery Slot [BAT0] (battery present)
[   21.500000] ACPI: AC Adapter [AC] (on-line)
[   21.516000] pcc_acpi: loading...
[B][   21.676000] speedstep_centrino: no version for "struct_module" found: kernel tainted.
[   21.676000] speedstep_centrino: version magic '2.6.20.3-ubuntu1 SMP mod_unload 586 ' should be '2.6.20-15-386 mod_unload 486 '
[   21.704000] speedstep_centrino: version magic '2.6.20.3-ubuntu1 SMP mod_unload 586 ' should be '2.6.20-15-386 mod_unload 486 '[/B]
[   25.584000] [drm] Initialized drm 1.1.0 20060810
[   25.584000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.588000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   26.280000] ppdev: user-space parallel port driver
[   26.516000] apm: BIOS not found.
[   27.160000] Bluetooth: L2CAP ver 2.8
[   27.160000] Bluetooth: L2CAP socket layer initialized
[   27.332000] Bluetooth: RFCOMM socket layer initialized
[   27.332000] Bluetooth: RFCOMM TTY layer initialized
[   27.332000] Bluetooth: RFCOMM ver 1.8
[   38.524000] NET: Registered protocol family 10
[   38.524000] lo: Disabled Privacy Extensions
[   38.524000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   63.368000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   64.416000] ieee80211_crypt: registered algorithm 'TKIP'
[   79.332000] eth1: no IPv6 routers present


O.k. see below - I think that is what you need - what about SMP - I've got a Pentium M Dothan pinmodded to Sonoma (400 to 533 FSB)

> root@felix-laptop:~# modprobe speedstep_centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.20-15-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): Invalid module format
root@felix-laptop:~# modprobe -r speedstep_centrino
root@felix-laptop:~# modprobe speedstep_centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.20-15-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): Invalid module format
root@felix-laptop:~# dmesg |tail -n30
[   21.128000] input: Lid Switch as /class/input/input7
[   21.132000] ACPI: Lid Switch [LID]
[   21.156000] input: Power Button (CM) as /class/input/input8
[   21.160000] ACPI: Power Button (CM) [PBTN]
[   21.184000] input: Sleep Button (CM) as /class/input/input9
[   21.188000] ACPI: Sleep Button (CM) [SBTN]
[   21.484000] ACPI: Battery Slot [BAT0] (battery present)
[   21.500000] ACPI: AC Adapter [AC] (on-line)
[   21.516000] pcc_acpi: loading...
[   21.676000] speedstep_centrino: no version for "struct_module" found: kernel tainted.
[   21.676000] speedstep_centrino: version magic '2.6.20.3-ubuntu1 SMP mod_unload 586 ' should be '2.6.20-15-386 mod_unload 486 '
[   21.704000] speedstep_centrino: version magic '2.6.20.3-ubuntu1 SMP mod_unload 586 ' should be '2.6.20-15-386 mod_unload 486 '
[   25.584000] [drm] Initialized drm 1.1.0 20060810
[   25.584000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.588000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   26.280000] ppdev: user-space parallel port driver
[   26.516000] apm: BIOS not found.
[   27.160000] Bluetooth: L2CAP ver 2.8
[   27.160000] Bluetooth: L2CAP socket layer initialized
[   27.332000] Bluetooth: RFCOMM socket layer initialized
[   27.332000] Bluetooth: RFCOMM TTY layer initialized
[   27.332000] Bluetooth: RFCOMM ver 1.8
[   38.524000] NET: Registered protocol family 10
[   38.524000] lo: Disabled Privacy Extensions
[   38.524000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   63.368000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   64.416000] ieee80211_crypt: registered algorithm 'TKIP'
[   79.332000] eth1: no IPv6 routers present
[ 1045.148000] speedstep_centrino: version magic '2.6.20.3-ubuntu1 SMP mod_unload 586 ' should be '2.6.20-15-386 mod_unload 486 '
[ 1147.856000] speedstep_centrino: version magic '2.6.20.3-ubuntu1 SMP mod_unload 586 ' should be '2.6.20-15-386 mod_unload 486 '



I think the problem lies in acpi cpufreq? I can't unload this module but as far as I understand either this module or speedstep_centrino is used by the kernel, not both.

---

### Post by spoilerhead on 2007-04-27
please try with with the generic kernel

then

```
modprobe -r speedstep-centrino
modprobe speedstep-centrino
dmesg |tail -n30
```

---

### Post by extremecarver on 2007-04-27
it doesn't look much better. -- This is what it gives with my own compiled 110kb speedstep_centrino - See post below for your 117kb speedstep_centrino.
I've tried your guide in german again using the newest patch from ubuntuusers.de and compiled my own speedstep_centrino but it didn't work either. 
When trying to use the patch for vanilla I get failures too.
It looked the same when using a no-sources kernel 2.6.20no2 (the laptop patches includes linux phc 0.3pre) I compiled myself. I don't won't to go back to dapper - but there it worked (with a custom compiled vanilla beyond sources patched kernel 2.6.16), as under windows.

> felix@felix-laptop:~$ sudo modprobe speedstep-centrino
Password:
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.20-15-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): Invalid module format
felix@felix-laptop:~$ dmesg |tail -n30
[   20.588000] input: Power Button (CM) as /class/input/input5
[   20.588000] ACPI: Power Button (CM) [PBTN]
[   20.616000] input: Sleep Button (CM) as /class/input/input6
[   20.616000] ACPI: Sleep Button (CM) [SBTN]
[   20.916000] ACPI: Battery Slot [BAT0] (battery present)
[   20.996000] ACPI: AC Adapter [AC] (off-line)
[   21.012000] pcc_acpi: loading...
[   21.192000] speedstep_centrino: version magic '2.6.20.3-ubuntu1 mod_unload 486 ' should be '2.6.20-15-generic SMP mod_unload 586 '
[   21.224000] speedstep_centrino: version magic '2.6.20.3-ubuntu1 mod_unload 486 ' should be '2.6.20-15-generic SMP mod_unload 586 '
[   29.264000] ppdev: user-space parallel port driver
[   29.476000] apm: BIOS not found.
[   30.096000] Bluetooth: L2CAP ver 2.8
[   30.096000] Bluetooth: L2CAP socket layer initialized
[   30.232000] Bluetooth: RFCOMM socket layer initialized
[   30.232000] Bluetooth: RFCOMM TTY layer initialized
[   30.232000] Bluetooth: RFCOMM ver 1.8
[   83.172000] [drm] Initialized drm 1.1.0 20060810
[   83.176000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   83.176000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   88.552000] NET: Registered protocol family 10
[   88.552000] lo: Disabled Privacy Extensions
[   88.552000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   98.280000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  108.848000] eth1: no IPv6 routers present
[  123.496000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  123.504000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  123.560000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  125.860000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  140.004000] eth1: no IPv6 routers present
[  462.412000] speedstep_centrino: version magic '2.6.20.3-ubuntu1 mod_unload 486 ' should be '2.6.20-15-generic SMP mod_unload 586 '


---

### Post by extremecarver on 2007-04-27
Here you go - didn't make it better (your 117kb speedstep_centrino entered, restarted pc, then the following, opointstable still not present).

> 
felix@felix-laptop:~$ dmesg |tail -n30
[   21.344000] No dock devices found.
[   21.384000] ibm_acpi: ec object not found
[   21.432000] input: Lid Switch as /class/input/input4
[   21.436000] ACPI: Lid Switch [LID]
[   21.464000] input: Power Button (CM) as /class/input/input5
[   21.464000] ACPI: Power Button (CM) [PBTN]
[   21.492000] input: Sleep Button (CM) as /class/input/input6
[   21.492000] ACPI: Sleep Button (CM) [SBTN]
[   21.792000] ACPI: Battery Slot [BAT0] (battery present)
[   21.812000] ACPI: AC Adapter [AC] (off-line)
[   21.996000] pcc_acpi: loading...
[   25.580000] [drm] Initialized drm 1.1.0 20060810
[   25.584000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.584000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   26.256000] ppdev: user-space parallel port driver
[   26.452000] apm: BIOS not found.
[   27.076000] Bluetooth: L2CAP ver 2.8
[   27.076000] Bluetooth: L2CAP socket layer initialized
[   27.152000] Bluetooth: RFCOMM socket layer initialized
[   27.152000] Bluetooth: RFCOMM TTY layer initialized
[   27.152000] Bluetooth: RFCOMM ver 1.8
[   42.872000] NET: Registered protocol family 10
[   42.872000] lo: Disabled Privacy Extensions
[   42.872000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   53.572000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   63.884000] eth1: no IPv6 routers present
[  121.352000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  121.424000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  123.684000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  137.744000] eth1: no IPv6 routers present
felix@felix-laptop:~$ sudo modprobe -r speedstep_centrino
Password:
felix@felix-laptop:~$ sudo modprobe speedstep_centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.20-15-generic/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): Device or resource busy
felix@felix-laptop:~$ dmesg |tail -n30
[   21.344000] No dock devices found.
[   21.384000] ibm_acpi: ec object not found
[   21.432000] input: Lid Switch as /class/input/input4
[   21.436000] ACPI: Lid Switch [LID]
[   21.464000] input: Power Button (CM) as /class/input/input5
[   21.464000] ACPI: Power Button (CM) [PBTN]
[   21.492000] input: Sleep Button (CM) as /class/input/input6
[   21.492000] ACPI: Sleep Button (CM) [SBTN]
[   21.792000] ACPI: Battery Slot [BAT0] (battery present)
[   21.812000] ACPI: AC Adapter [AC] (off-line)
[   21.996000] pcc_acpi: loading...
[   25.580000] [drm] Initialized drm 1.1.0 20060810
[   25.584000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.584000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   26.256000] ppdev: user-space parallel port driver
[   26.452000] apm: BIOS not found.
[   27.076000] Bluetooth: L2CAP ver 2.8
[   27.076000] Bluetooth: L2CAP socket layer initialized
[   27.152000] Bluetooth: RFCOMM socket layer initialized
[   27.152000] Bluetooth: RFCOMM TTY layer initialized
[   27.152000] Bluetooth: RFCOMM ver 1.8
[   42.872000] NET: Registered protocol family 10
[   42.872000] lo: Disabled Privacy Extensions
[   42.872000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   53.572000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   63.884000] eth1: no IPv6 routers present
[  121.352000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  121.424000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  123.684000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  137.744000] eth1: no IPv6 routers present
felix@felix-laptop:~$ 

---

### Post by spoilerhead on 2007-04-28
hm, so no matter what patch you use on what kernel in feisty, it doesn't work?
then [file a bug please]("https://www.dedigentoo.org/trac/linux-phc/")
there mus be a regression somewhere in the code then

---

### Post by extremecarver on 2007-04-28
After reading around for hours I think it's a known problem with broken bios voltage tables and might be fixed in linux-phc-0.3 which promises to support acpi-cpufreq (which works well for my laptop). So I'm gonna wait till it comes out and if it then still doesn't work file another bug. The problem is that this could be a bug in ubuntu too - there are some bugs at launchpad mentioned about speedstep-centrino not loading since edgy.

---

### Post by D-- on 2007-04-28
That's fixed. What happened was that there WAS NO speedstep-centrino.ko for like 6 kernel updates. So compiling it and sticking it in did nothing. If you tried to compile more and overwrite more of the cpufreq files, cpufreq itself totally broke.

I have a thread on PHC and Feisty over in the closed Fesity dev forum. I posted a pre-compiled speedstep-centrino.ko binary.

[http://ubuntuforums.org/showthread.php?t=364321](http://ubuntuforums.org/showthread.php?t=364321)

Check the second post, then do a '$ uname -a'. If you are listed as a safe kernel, you should be able to drop it in just fine. I personally tested in in every single kernel update listed there, and many others have reported success. If your kernel HAS a speedstep-centrino.ko, then that is the only file you need replace.

Lastly, be sure you follow the script installation instructions in PHC. If you have followed the script install exactly and remembered to uncomment the line it tells you to, you should be fine.

If this still doesn't work for you, then your machine is having a much deeper problem than PHC.

---

### Post by extremecarver on 2007-04-28
Well I'm just recompiling a kernel with speedstep-centrino with yes and not as a module - lets see how it goes. Temperature is rising to 79° - while with full load under windows undervolted I've never had over 62° C. (room temp 24° C.).

Edited:
I just tried the speedstep-centrino.ko posted by D-- which didn't want to work for me either - nor in i386 or generic. 
Again kernel panic with my kernel so I just give up now.
The bug I read about was actually introduced by 2.6.18 kernel branch and I think by now really affects my laptop. Do you think it's possible to use 2.6.17 kernel with feisty, in that case I could just get the edgy kernel and patch it for my proper use (including patching to newest alsa which I need for my usb soundcard).

---

### Post by D-- on 2007-05-01
There's no kernel panic unless you patch the speedstep-centrino.ko file?

That's really odd. Even when I totally broke CPUFreq's module, I was still able to boot without a kernel panic ... I just had no CPUFreq.

---

### Post by Djembe on 2007-05-01
I'm having a problem with the 2.6.20-15 kernel versions (it happens on both 386 & generic).  I copied your speedsted-centrino.ko to /lib/modules/2.6.20-15-386/kernel/arch/i386/kernel/cpu/cpufreq and also to /lib/modules/2.6.20-15-generic/kernel/arch/i386/kernel/cpu/cpufreq just in case.  Then I ran ./configure in the /home/rob/linux-phc-0.2.9/utils/measurefreq directory, which seemed to work fine, but when I run make, I get this:
```
rob@Avalon:~/linux-phc-0.2.9/utils/measurefreq$ make
make  all-recursive
make[1]: Entering directory `/home/rob/linux-phc-0.2.9/utils/measurefreq'
Making all in src
make[2]: Entering directory `/home/rob/linux-phc-0.2.9/utils/measurefreq/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -MT measurefreq.o -MD -MP -MF ".deps/measurefreq.Tpo" -c -o measurefreq.o measurefreq.cpp; \
        then mv -f ".deps/measurefreq.Tpo" ".deps/measurefreq.Po"; else rm -f ".deps/measurefreq.Tpo"; exit 1; fi
In file included from measurefreq.cpp:28:
/usr/include/asm/msr.h:7:4: error: #error asm-i386/msr.h does not exist in the i386 architecture
measurefreq.cpp: In function &#8216;void MeasureFreq(arguments)&#8217;:
measurefreq.cpp:196: error: &#8216;rdtsc&#8217; was not declared in this scope
make[2]: *** [measurefreq.o] Error 1
make[2]: Leaving directory `/home/rob/linux-phc-0.2.9/utils/measurefreq/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rob/linux-phc-0.2.9/utils/measurefreq'
make: *** [all] Error 2

```What do I need to fix, and how do I fix it?

---

### Post by extremecarver on 2007-05-01
> **D-- said:**
> There's no kernel panic unless you patch the speedstep-centrino.ko file?

That's really odd. Even when I totally broke CPUFreq's module, I was still able to boot without a kernel panic ... I just had no CPUFreq.
Nope - I must have made a mistake in xconfig - disabling something too much, but couldn't find the mistake. Nothing to do with speedstep-centrino - I'm going to give CPUPW a try in order to undervolt.

---

### Post by jimmyp on 2007-05-03
> **Djembe said:**
> 
```
rob@Avalon:~/linux-phc-0.2.9/utils/measurefreq$ make
make  all-recursive
make[1]: Entering directory `/home/rob/linux-phc-0.2.9/utils/measurefreq'
Making all in src
make[2]: Entering directory `/home/rob/linux-phc-0.2.9/utils/measurefreq/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I..     -g -O2 -MT measurefreq.o -MD -MP -MF ".deps/measurefreq.Tpo" -c -o measurefreq.o measurefreq.cpp; \
        then mv -f ".deps/measurefreq.Tpo" ".deps/measurefreq.Po"; else rm -f ".deps/measurefreq.Tpo"; exit 1; fi
In file included from measurefreq.cpp:28:
/usr/include/asm/msr.h:7:4: error: #error asm-i386/msr.h does not exist in the i386 architecture

```What do I need to fix, and how do I fix it?

I am guessing that the problem is that asm-i386/msr.h can't be found.  Doing an apt-file search asm-i386/msr.h reveals that this file is in the linux-headers package for your kernel.  So install that package and give it another shot.

---

### Post by extremecarver on 2007-05-16
For me switching over to 2.6.22rc1 CK patchset, 0.2.10 Linux-Phc and some patches from linuxpowertop and now undervolting does work. I retried 2.6.16 beyond kernel which worked too. 2.6.17 to 2.6.21 aren't working on my laptop however.

I had to use cpu-freq centrino as a module as it wouldn't work directly in the kernel. Now I only need to get my wireless back with 2.6.22 and Intel 2925ABG - simply copying over the firmware drivers like before with older vanilla kernels didn't do the trick. -solved Never Compile the IPW2200 as built-in cause it will only work as a module.

Nevertheless even with the newest patches from linuxpowertop my laptop uses minimum 10Wats vs 8Wats on Windows (wireless off, Screen dimmed to a value that only works without much surrounding light). I noticed that disabling wireless enables the CPU to access C3 and C4 state much longer and more often saving about 1 Watt more than in windows (difference in windows about 1 Watt vs 2 Watts in Linux). Seems that IPW2200 is not very energy efficient under linux as it stresses the CPU a lot.

---

### Post by extremecarver on 2007-05-17
> **jimmyp said:**
> I am guessing that the problem is that asm-i386/msr.h can't be found.  Doing an apt-file search asm-i386/msr.h reveals that this file is in the linux-headers package for your kernel.  So install that package and give it another shot.

Try with 0.2.10 linux-phc there was a bug in 0.2.9

---

### Post by ruisselet on 2007-07-08
I have made a small package with the following goals:

* install init scripts for undervolting

* be able to use PHC without (re)compiling the whole kernel

For this, the package contains a script, linux-phc-install, that will compile the patched speedstep-centrino module against a certain kernel version (the running version by default), provided the kernel-headers are available.

It tested it succesfully on ubuntu/feisty with 2.6.20-16-generic and debian/etch with 2.6.18-3-686.

You can get the package at:
[http://bonniot.dyndns.org/pub/phc/linux-phc-install_0.2.10-1_i386.deb](http://bonniot.dyndns.org/pub/phc/linux-phc-install_0.2.10-1_i386.deb)

Comments are welcome.

Enjoy!

---

### Post by extremecarver on 2007-07-09
Your deb doesn't install on 7.10 with 2.6.22 kernel.

error message : subprocess post-installation script returned error exit status 1.
Can anyone confirm this for 7.10?

---

### Post by info2 on 2007-07-15
There is a new Version available (but not yet in SVN).
Link:[https://www.dedigentoo.org/bdz/linux-phc/linux-phc-0.3.0-pre1.tar.gz](https://www.dedigentoo.org/bdz/linux-phc/linux-phc-0.3.0-pre1.tar.gz)

This patch now also introduces changes to acpi-cpufreq as a replacement to the speedstep-* modules.
The Interface changed a bit. You should take a look to the Website or ask in the Chatroom.

Also there is a GUI in GTK+ written by me ( cmichael ) that is able ob setting and checking values and restoring them on load.

I'm using Ubuntu 7.10 with kernel 2.6.22 and the acpi-cpufreq module on a core2duo T7200 and its working fine.

---

### Post by Black16V on 2007-07-24
I patched the 2.6.22 Kernel successfull. But now, how can i change the voltage?


I have calculated the new vids for my Pentium M (715) (stable voltages (mV):1196 1100 1004 908 812)
with this formula: VID = (voltage-700)/16

new: vids: 31 25 19 13 7
standard vids: 40 33 28 23 18

But why i can't set  the vid below 18???

Is a patch for the 2.6.22 available, where i can set the voltages with the REAL values?


> Also there is a GUI in GTK+ written by me ( cmichael ) that is able ob setting and checking values and restoring them on load.

I tried to checkout PHCtool from the repository, but it failed (no access), Is there a DEb package avaible?

---

### Post by info2 on 2007-08-15
Hello, I'm sorry that i didn't answered earlier.

>>I patched the 2.6.22 Kernel successfully. But now, how can i change the voltage?
You'll find some read only and some read/write files in /sys/devices/system/cpu/cpu0/cpufreq
To set new values use phc_vids or phc_controls. Refer to the wiki for a more detailed howto.

>>I have calculated the new vids for my Pentium M (715)...
>>new: vids: 31 25 19 13 7
>>standard vids: 40 33 28 23 18
>>But why i can't set the vid below 18???
Are you sure that you can not set VIDs below 18? How did you find out?
Intel Core and Core2 - CPUs are known to have a hardware limitation like that, but not Pentium Mobile.
You can meet us in the irc-channel on freenode (##linux-phc) if you need some help.

>>Is a patch for the 2.6.22 available, where i can set the voltages with the REAL values?
With the upcoming release of linux-PHC we changed the sysfs interface to show VIDs instead of Voltages. The problem with those voltages is that we have to estimate the correct formula for each type of CPU because they differ. This may produce wrong values. The calculating of voltages can be done by userland tools because it's easier to update them with new formulas.

>>I tried to checkout PHCtool from the repository, but it failed (no access), Is there a DEb package >>avaible?
No and it's not necessary because it can run from any directory you store it, but everyone creating a deb is very welcome.
I don't know why you could not access it.
Have you tried
svn co [https://www.dedigentoo.org/svn/linux-phc/trunk/src/utils/phctool](https://www.dedigentoo.org/svn/linux-phc/trunk/src/utils/phctool)
?

If there still are problems you can meet me in the irc channel.

I hope i can help you.

---

### Post by D-- on 2007-09-10
Would you be willing to post your patched modules for the Gutsy kernel?

I had a nightmare getting PHC working in Feisty, and a lot of people with similar problems used the patched speedstep file I attached here in the forum.

I've been itching to start testing Gutsy, but my laptop just can't handle life without underclocking, especially in Linux, where the video drivers for my card don't support power save. I don't want to struggle through that again, and last I heard, PHC is never making it into the Linux kernel or apt.

---

### Post by Djembe on 2007-10-20
Undervolting in Gutsy seems fairly painless, with one exception.  Following the directions contained here: [https://www.dedigentoo.org/trac/linux-phc/wiki/phc_howto_ubuntu_001](https://www.dedigentoo.org/trac/linux-phc/wiki/phc_howto_ubuntu_001) successfully undervolts my Pentium M 750 (1.86 Ghz), however the voltage changes are only active for the current session.  I haven't figured out how to make the changes persist after a restart.  The Edgy HOWTO guide accomplishes this via a file that is not installed in the Gutsy version, and I am not sure what an appropriate method would be to make the voltage changes persistent.  Any suggestions?

---

### Post by Maulwuff on 2007-10-21
in feisty I did undervolting by setting the voltages in 
/sys/devices/system/cpu/cpu0/cpufreq/op_points_table
but this file has gone in gutsy.
Even after applying the speedstep_centrino.ko by D-- this file is not there. 
Is this file missing on a fresh gutsy, too? I did upgrade to gutsy.

---

### Post by Djembe on 2007-10-21
> **Maulwuff said:**
> in feisty I did undervolting by setting the voltages in 
/sys/devices/system/cpu/cpu0/cpufreq/op_points_table
but this file has gone in gutsy.
Even after applying the speedstep_centrino.ko by D-- this file is not there. 
Is this file missing on a fresh gutsy, too? I did upgrade to gutsy.

Okay, I'm figuring out some things.  the file op_points_table is deprecated and has been replaced by phc_controls.  I think I've figured out how to get undervolting to work on startup now!  I'm going to test it and if it works, I'll post my method.

---

### Post by Maulwuff on 2007-10-22
Ok, I figured out, why it is missing:
This has chanched from .19 to .20 kernel.
see the gentoo-wiki for further instructions and more information behind those FIDs and VIDs:
[http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU](http://gentoo-wiki.com/HOWTO_Undervolt_a_Pentium_M_CPU)

---

