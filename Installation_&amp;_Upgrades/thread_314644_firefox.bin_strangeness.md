---
title: "firefox.bin strangeness"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by gtsmith on 2006-12-07
Here's one for y'all. I've had a solid Ubuntu install on my Dell 1505 laptop running for a few weeks now. ATI graphics with Beryl 0.1.3 running great, wireless card with WPA just fine, all peripherals configured and running fine. Two days ago I noticed my CPU (Core 2 Duo T7200) usage was at 50%. 
I checked the resource monitor and found that one CPU was pegged at 100% the other CPU hovered in the single digits. I checked the processes and found firefox.bin taking anywhere from 44% to 48% of the CPU. Firefox was open. I close firefox and of course the CPU usage dropped to normal. Reboot the box, launch firefox, and firefox.bin once again goes to 44-48%. Don't know what was going on...used the laptop yesterday and it ran fine but of course any time I ran firefox, CPU usage goes back up to 50%. 
Today, I was running the laptop, firefox doing her same strangeness, and I applied the updates to Beryl that Update Manager wanted me to. I reboot the box...just fine. I notice once again that firefox.bin is consuming 50% of CPU, so I reboot once more. This killed the box. It wouldn't progress more than ~20% of the Ubuntu progress at boot. It would just hang. I let it sit there for about 15 minutes and realized it was not going to change. So, I reboot again, this time my BIOS boot (you now, the time it takes to get through the BIOS boot screen) took about five times as long as normal. 
I panicked. Shut her down and threw back int he original restore disk (WinXP-yuck...but hey...thought I'd see what would happen). Did a restore in windows and all is fine (thought it might be a dieing harddrive). I'm going to reinstall Ubuntu tomorrow (I dread having to go all through the ATI and Wireless setup again, but hey what ya gonna do?). 

Anybody else experience kind of weirdness?

---

### Post by tophatandy on 2006-12-07
my firefox bin is currently at 0% usage.. with firefox running..

but:

I am missing half of my cpu processing speed..


I am **supposed** to be running near 2 Ghz (depending if I overclock or not)
I **am** running at 1.00044 Ghz..


dont know what is going on here..

my cpu is a AMDx64 3200+ if anyone has an answer for me..

I would suggest a reinstall and then dont update firefox to 2.0

(if that is what you did)

2.0 seems still kindof unstable-ish

if you were just running the standard firefox that came with ubuntu, then consider updating to 2.0

(aka: dont do what you did before)

sorry about the trouble and best of luck to you.

---

### Post by jgcamp99 on 2006-12-08
I've experienced similar with my Athlon XP 3200+. I'm using Edgy and I've noticed that Edgy is exactly as it's name implies. Recently, updates to Xine, Gnome and Xorg (the latter two appeared and were updated earlier this evening), have also improved stability. FF has crashed on occasion before.

Edgy is moving more towards the stability and reliability that I was so impressed with in Dapper.

Anyhow, that FF cpu usage, it's almost as if it locks itself up and doesn't  release the cpu time. Maybe it's the internet, website and code that is effecting FF that way. It's gotten to the point, that I don't know which websites are safe anymore. It's driven by advertising and so on, so the motivation is there for the websites to literally attack you with popups and advertising.

---

### Post by promet on 2007-02-07
Hi,

I am also using Edgy and have had similar difficulties with FF and CPU usage. I do a lot of streaming media and this seems to be particularly bad when I leave FF open to listen to/watch long streams, it seems to get less stable over longer instances of use.

I like Edgy, but as you say, it is aptly named...

If anyone finds anything definitive on this please do drop a line.

---

