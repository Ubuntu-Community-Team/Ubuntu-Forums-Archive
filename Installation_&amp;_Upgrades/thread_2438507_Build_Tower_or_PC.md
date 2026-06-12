---
title: "Build Tower or PC"
date: 2020-03-13
forum: Installation &amp; Upgrades
---

### Post by oneleded on 2020-03-13
i bought my 1st PC in 2000. it was also my last. The hand me down Dell i2002 model is on it's last Leg. 2GB of memory. i could ad 2GB more, not much point. i am way overdue for a new machine. i plan on building it myself. way cheaper. this is what i got so far; AMD Ryzen 5  1600, Sabrent Rocket Q NVMe PCIe internal SSD 1TB, still working on workstation motherboard, i dont game. i just get online. i already have monitor, two RW Sata ROM's,. i got cabinet lined out, or case.
i got to figure out USB, SATA, NVMe, PCIe, on workstation motherboard. been doing some research, with a little help. finding an ergonomic keyboard when you put linux friendly in the search is problematic. i bought "microsoft natural multi media keyboard" in 2005. my niece broke the kickstands off the back of keyboard when she was young, plus my angle of attack is wider than is was years ago, my elbows got more bowlegged in old age.[I will look up the right words later]. power supply is easy enough to pick out. guess im stuck on compatible, workstation motherboard, and how much USB i will need, USB2 and USB3. im in the early planning stages. if this is not the right place to post, let me know. i forgot to mention 8GB of ram is better than 2GB, should i need to add more, i need more slots to put in memory. DDR4 i think. my memory needs DDR4 too. to much white matter. they don't make that yet. ;~}

---

### Post by CatKiller on 2020-03-13
The Ryzens are great. I'm not sure why you'd pick the 1600, though, rather than the newer models. They've had some big improvements as they've developed. 

Knowing which processor you're going with gets you most of the way to knowing which motherboard; there are only a handful of chipsets to choose from, and then it's picking a manufacturer that you find reputable and balancing which features you want against how much you want to spend. The choice of motherboard determines what type of RAM you need. PC Part Picker is a useful tool: it will remember where you got to on selecting parts and will highlight any incompatibilities. For RAM specifically each motherboard will have a QVL of modules that have been tested and shown to work properly. 

I'd recommend 16 GB to everyone in a new build, unless they have a particular need for 32 GB. There's not really a reason to have less these days, particularly if you're aiming for longevity.

---

### Post by him610 on 2020-03-13
Hello oneleded,
I use my computer much the same as you. Just completed a build myself. You can model your build and check that all of the components are compatible here, [https://pcpartpicker.com/]("https://pcpartpicker.com/") without spending a dime.
I usually begin with asking myself, 'how large of a case do I want?" Recent build was micro-ATX, the two before that were mini-ITX. As soon as I had finished the build, I asked myself, 'Why didn't I build this one as mini-ITX?' You can buy comparable motherboards in ATX, micro-ATX, mini-ITX sizes from most, if not all of the manufacturers. You already have your APU/CPU, NVME and SSD drives.
I reuse what I can on new builds: monitors, keyboards, mice, graphics cards, SSD, and HDD. In fact, my installed graphics cards were all castoffs from friends and relatives. Recommend you consider modular or semi-modular power supply.
Good luck with your build.

---

### Post by oldfred on 2020-03-13
Use pcpartpicker.
[https://pcpartpicker.com/list/](https://pcpartpicker.com/list/)
You also can see other builds with similar parts.

It saved me from buying wrong drive. I was building a small form factor system and 3.5" drive I chose would not fit. Had to use laptop type drive. I did not necessarily buy from suggested vendor, but it was good to know prices.
Newer motherboards support M.2 NVMe drives, but you have to check. Early M.2 drives were SATA only and replaced one of the available SATA ports.

I made a mistake on earlier build. I had monitor with DVI & VGA in and bought a motherboard with HDMI & Display port out. Had to add a low cost video card. Then found cable that would work to convert as chip's internal video was higher rated than older video card.

---

### Post by oneleded on 2020-03-14
i dont game just get online. i thought that processor would get me by and save some money. i'll check the new ones. thanks. i got 2 GB on 2002 dell. i thought 8GB would be enough. i'll see how much 16GB cost probably not much more.

---

### Post by oneleded on 2020-03-14
thanks for the advice

---

### Post by oneleded on 2020-03-14
LVI Attack Hits Intel SGX - Defeats Existing Mitigations, More Performance Hits
The Brutal Performance Impact From Mitigating The LVI Vulnerability
guess ya already seen this. thought id post it anyway. i dont know what. it means
bad for intel. Zen 2 seems to be all right.

---

### Post by TheFu on 2020-03-14
Be careful with Sabrent storage.  They haven't been helpful n providing endurance numbers for their SSDs.   contacted their support team who refused to provide those specs.  Best to stick with more reputable SSDs, like from  Samsung.

Ryzen 1600 is fine, but mainly if budget constrains you.  A 20 yr old PSU needs to be replaced too.
Ryzen only supports DDR4.  it likes faster DDR4, so 3200 to start.  Should be about $70 for 16G.
Get a reputable Samsung SSD for $50 and 2TB HDD more for $40.
Ryzen drives the compatible MB  - B450, X370, X470, X570 .. depending on budget.
You'll need a GPU.  i have an nVidia 1030, but would look at AMD GPUs more closely if in the market today.

My Asus B450 MB has 2 m.2 storage slots.  One works as 4x NVMe.  The other as SATA and if used at all, the 6-SATA ports become only 4. Read the MB manual carefully, before purchase.  Beware that some MB vendors have next to ZERO support for Linux.  That usually doesn't matter ...er ... until it does, totally, completely, no way around the issue.

if you keep a computer 20 yrs, wouldn't you rather get 2x the RAM you think is needed today, when it is cheap?
Here's my Ryzen 2600 build
```

           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: **ASUSTeK** model: **ROG STRIX B450-F GAMING** v: Rev 1.xx
           Bios: American Megatrends v: 2801 date: 09/18/2019
CPU:       Hexa core AMD **Ryzen 5 2600** Six-Core (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 3400 MHz 1: 1376 MHz 2: 1376 MHz 3: 1381 MHz
           4: 1377 MHz 5: 1450 MHz 6: 1546 MHz 7: 1376 MHz 8: 1376 MHz
           9: 1533 MHz 10: 1375 MHz 11: 1375 MHz 12: 1544 MHz
Graphics:  Card: NVIDIA GP108 [GeForce GT 1030]
           Display Server: X.Org 1.19.6 driver: nvidia
           Resolution: 1920x1080@60.01hz
           GLX Renderer: N/A GLX Version: N/A
...
Network:   Card: **Intel I211 Gigabit Network** Connection driver: igb
           IF: enp3s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1262.3GB (35.4% used)
           ID-2: /dev/sdb model: **Micron_1100_MTFD** size: 512.1GB
..
Info:      Processes: 372 **Uptime: 15 days** Memory: 11857.4/**16033.0MB**
           Client: Shell (bash) inxi: 2.2.35
```
Very stable. 6 cores, 12 threads.

I waited until prices had dropped about 50% before building.  Prices have dropped another 25% since that time.  The MB+RAM+CPU should be under $220 now, maybe cheaper.

---

### Post by oneleded on 2020-03-15
i like my  2 Seagate HDD, what i got now. i was planning for DDR4. still dont know what i'm doing yet. just in the planning stages, ZERO support for Linux. That usually doesn't matter ...er ... until it does, totally, completely, no way around the issue. seems like a constant everywhere. a work station motherboard is fine with me, should i find one. will do/read the MB manual. dont know if i will understand, but will look for linux support . i'm 64, looking for something till i can't type.[a magic number for amd]64. i still got part's i dont have to buy. as my monitor should still work. sound system. use it very little any way, don't know if printer will work, HP deskjet 5150, great on ink. Logitec wireless mouse. [they, Logitec, quit making this a long time ago] was $75.00. used or new in package are high dollar., same as printer. comfortable wireless mouse. The best for me. i just want to save some money. who dont.
thanks for advice
PS, if you ever watch NCIS, that is the mouse on the show. i dont remember what model it is. best i can remember is, wireless optical marble mouse. was 2002 when i got it or so.

---

### Post by him610 on 2020-03-15
> i was planning for DDR4
Recommend you check the support section of the motherboard manufacturer you decide on. They normally have listings of recommended memory, storage devices, and processors.

---

### Post by TheFu on 2020-03-15
Ryzen MBs don't accept anything except DDR4. Ryzen used to be picky about specific RAM models. That hasn't been the situation for at least 2 yrs.  I'm running non-approved RAM, G.Skill 3200 @ 3200. The XMP stuff profiles work.

If your monitor isn't DP or HDMI, you'll probably need a new one.  Current video cards don't support VGA output.
Wireless mice/keyboards scare me.  Any RF scares me due to non-security. Same for Wifi and Bluetooth, though with wifi at least we can run a VPN. No wireless stuff here without a VPN. Hate to be proven right when so many people make the mistake of trusting wifi/BT/RF stuff when they shouldn't. Got hacked over bluetooth about 5 yrs ago. Never again.  Also, be careful with those DECT-6 cordless phone systems. It is standardized for a reason. No wiretap warrant needed, my friends.

I trashed inkjets decades ago, switched to laser printing.  The ink for lasers doesn't dry out every year like with inkjets. Plus the laser's are just as cheap these days.

As for keyboards, I use a $0.50 used IBM 101M keyboard and have 2 spares in the closet. Picked up all three at a computer swap meet in the 1990s.  All that has changed all this time is which adapter is needed for the DIN plug for each keyboard. Switched to a USB "Y" connector around 2010 from a DIN-to-PS2 connector. 

All these tiny, little, choices today, matter.

---

### Post by oneleded on 2020-03-16
the inkjet dont use too much ink, i got refill bottles. started checking GPU out. i live out in the country, don't expect wireless mouse will hurt me. i needed some Pot's for an amplifier. guy wanted me to give credit card number over the phone. its not a house phone. wireless. i wouldn't do it.  progress is moving into the county.
 monitor is HDMI. 
Are wireless laptop's a problem for hacking? seems like they would be. i think they would be. along with satellite internet.

---

### Post by oneleded on 2020-04-04
i bought the ryzen 5 1600af. looking ATX, x470 motherboards. i think i want a stable bios, good heat sinks, an port's, plus low wattage, thats all i can remember, at this moment.. reviews are mostly for gaming. i don't game., wish i could, being able to go outside is more important, anyway, or, in/through the woods. need spray's for that, least 40% deet. least ya dont get ticks, unless ya count certain people.
i have a passion for linux. lubuntu, an, some other distro's. nothing to do with windows, i had my fill. XP was my last one.
well, im done ranting.

---

### Post by TheFu on 2020-04-04
1600af - NICE!  Most people wouldn't know how smart that was for performance AND budget.

---

### Post by oneleded on 2020-04-07
> **TheFu said:**
> 1600af - NICE!  Most people wouldn't know how smart that was for performance AND budget.
i dont want to tell them, in case i need, or, want another one. for the price.  on the side, i dont feel greedy, an i'm willing to share here. or i wouldn't post it.
y'all been very nice to me.

---

### Post by mrdc76 on 2020-04-07
> **oneleded said:**
> i bought the ryzen 5 1600af. looking ATX, x470 motherboards. i think i want a stable bios, good heat sinks, an port's, plus low wattage, thats all i can remember, at this moment.. reviews are mostly for gaming..

Don't buy a X-series motherboard for Ryzen if you plan to use your computer for a long time. They have a small fan for the chipset that might break or start making noise. B450s do not have the chipset fan.

---

### Post by oneleded on 2020-04-09
too late, i all ready did.
msi performance  x470 gaming plus
sabrent rocket q 1TB NVMe PCIe M.2 2880 internal high performance SSD
AMD Ryzen 5 1600AF
i think i might need a heat sink for the sabrent rocket
i'm looking for a case, preferably white, of some sort
MB is ATX
i got 2 RW drives, both internal, and SATA., i bought a while back.
i found a 72,000 rpm HDD for about $37.oo, least i think. Seagate Barracuda, 1TB
that should put me close to $450 mark, excluding the case, and extra wiring, maybe fans.
im going low budget, and dont know what im doing.

---

### Post by TheFu on 2020-04-09
sabrent is an "iffy" provider. Same for Seagate drives between 750G and 7TB. Iffy with documented issues. There aren't any 72,000 rpm HDDs, BTW. ;)  Barracuda's had terrible overheating issues and they were very noisy.

Seems like an expensive MB for a $80 CPU.  I'd only do that if I definitely planned to move to a faster Ryzen in a few years.

Low budget to me would be sub-$250.  Usually, I pick a CPU, which mandates a family of MB.  For the MB, I seek specific capabilities (Intel GigE NIC; 6-10 SATA ports, 1 NVMe x4 slot) and specific things I don't want (no WiFi EVER!).  Lastly, is RAM.  Ryzen likes 3200Mhz RAM. I need to get 16GB more soon. Been running out of RAM and swap on my main VM host, but have plenty of CPU available for more work.  Fortunately, I "felt" the low RAM issue and was able to shutdown a VM, which freed 3G of RAM.  I'm down to 8 VMs and trying to move most of those into LXD containers. Just need to figure out the LXD storage stuff.

I have cases, PSUs, HDDs, etc.

---

### Post by oneleded on 2020-04-13
this is what i got so far;
MSI Performance x470 gaming PLUS
Sabrent Rocket Q  1 TB NVMe PCIe M.2 2880 Internal High Performance SSD
AMD Ryzen 5 1600AF
i got 2 sata RW drives on the side, an a monitor HDMI ready
i dont really need an HDD drive, an thought i might get another SSD drive, 1 TB Seagate 7200 RPM. it dont have to be Seagate
i need a case, compatible PSU, maybe some extra wiring attachments. i got some speakers also. maybe my keyboard will still work.
as far as OS, for some reason, linux is not mentioned. i got lubuntu now. they just mention Window's 10. i lost interest after XP.
dont want to catch up.
i dont game, cant do it. just trying to build a killer machine, on a low budget.
i left out a few parts, memory, and i need a card for vision,[not the proper term, maybe tomorrow].
graphics seems to come to mind. GPU maybe.
i gotta have enough room in the chassie/case. seems the card takes up some space, and is needed for Ryzen 5 1600AF.

---

### Post by CatKiller on 2020-04-13
> **oneleded said:**
> i need a case, compatible PSU,

Very cheap cases require a blood sacrifice every time you work in them. More expensive cases have their edges machined smooth, and use thicker metal, which makes them less hungry.

Fully modular PSUs make things a lot easier; you can just remove whichever cables you aren't using. PCPartPicker will show you how much power the components you've picked are likely to need.

> i left out a few parts, memory, and i need a card for vision,[not the proper term, maybe tomorrow].
graphics seems to come to mind. GPU maybe.

Yep, you'll need some RAM and a GPU.

For the GPU I'd recommend an AMD card that isn't too new, since you aren't gaming to push the performance limits. Nvidia graphics have the highest-end performance, and they're supported by their proprietary driver on the day of release, but the proprietary driver does things its own way. It takes a while for AMD support to trickle down through the distros to the end users, and a while after that till they perform as well as they can, but the drivers are open source so they integrate with the rest of the software ecosystem, and the mid-range hardware is competitive with Nvidia. If you get a card that isn't the latest-and-greatest, the support will have already gone through both the trickling and polishing phases.

> seems the card takes up some space

Most cards fit in most cases. The motherboard that you're going with is ATX, so your case isn't going to be tiny. The cards that are big are the monster cards that turn a lot of power into a lot of performance: they need the cooling, so they are long and take up multiple slots for the massive heatsinks they need (my GPU needs to shed 300 W of heat when it's going full tilt). More modest cards don't need the space. The length needs to fit into the distance between the back plate of the case and whatever you've got hanging off the front - drives and so on. The width (often given in slots) is how many slots on the motherboard you wouldn't be able to use because of the big fat GPU. You can also find versions of some models that *are* designed to go in tiny cases: at full tilt they tend to be noisier than the larger versions, since you have fewer fans trying to move the same amount of air to keep them cool, but you aren't planning to run your GPU at full tilt anyway.

---

### Post by oneleded on 2020-04-15
this case with power supply was suggested to me, "Raidmax Vortex V4 V4 ATX-404WUP" its really cheap and comes with 450Watt power supply.
it doesnt have the 12V to motherboard plug in, in case i want to overclock. i dont want to overclock now, maybe never. but i'd like to ability to.
my budget was $500.oo. i can go pass this though. i just dont want to go to far. 1st PC i built, it dont have to be great, but i want it to be good.
Now for a question. How do 5.25 bays translate into my rewrite drives? i dont understand the measurements. best i can figure, they are least 5.75 ins. wide,
my RW, Drives. DVD, RW.,  CD, RW ROM.
i want to make sure i understand this. is it like a 2"x4" in construction? the measurement was not exact. i helped frame many houses.
i am using part picker, it suggested the 450 watt power supply was wrong, missing the 12V to, power MB, for clocking.
learning as i go.
PS,  i dont care if the case is bigger., it just has to fit on my desk. tall x deep, dont bother me, too much, i wouldn't want it wider than 9".
my desk is crowded for lack of house keeping. we all got our quarks.

---

### Post by CatKiller on 2020-04-15
> **oneleded said:**
> Now for a question. How do 5.25 bays translate into my rewrite drives? i dont understand the measurements. best i can figure, they are least 5.75 ins. wide, my RW, Drives. DVD, RW.,  CD, RW ROM.

Drive bays are entirely standardised, and have been around for a *very* long time. There are three sizes - called 5¼", 3½" & 2½" - named after the size of floppy disc that would fit into them. Optical drives fit into a 5¼" drive bay. Spinning hard drives generally go in a 3½" bay, and SSDs go in a 2½" bay. You can also use the bays for accessories like fan controllers, extra ports, displays, and so on.

---

### Post by kurt18947 on 2020-04-15
You can get adapters to adapt devices to the bay size. For instance I have a 2.5" notebook drive in a 5.25" bay. I would certainly recommend a new power supply, My wife's PC recently quit, I figured out it was a dead power supply. Not really a surprise, that power supply had been in use for a several years. I bought a new power supply, installed it and ....... still no power. It seems that the failing power supply damaged the motherboard as well. So it wound up costing me a power supply, motherboard, processor and RAM. The motherboard was old enough (FM2 socket) that it would have been difficult to find a compatible replacement plus I didn't know how many components on the old motherboard were damaged. All due to a $40 power supply.

---

### Post by oneleded on 2020-04-15
> **CatKiller said:**
> Drive bays are entirely standardised, and have been around for a *very* long time. There are three sizes - called 5¼", 3½" & 2½" - named after the size of floppy disc that would fit into them. Optical drives fit into a 5¼" drive bay. Spinning hard drives generally go in a 3½" bay, and SSDs go in a 2½" bay. You can also use the bays for accessories like fan controllers, extra ports, displays, and so on.
that answers my question on many points. an i am glad to know.

---

### Post by oneleded on 2020-04-15
> **kurt18947 said:**
> You can get adapters to adapt devices to the bay size. For instance I have a 2.5" notebook drive in a 5.25" bay. I would certainly recommend a new power supply, My wife's PC recently quit, I figured out it was a dead power supply. Not really a surprise, that power supply had been in use for a several years. I bought a new power supply, installed it and ....... still no power. It seems that the failing power supply damaged the motherboard as well. So it wound up costing me a power supply, motherboard, processor and RAM. The motherboard was old enough (FM2 socket) that it would have been difficult to find a compatible replacement plus I didn't know how many components on the old motherboard were damaged. All due to a $40 power supply.
if there was a like button, i would. i dont do facebook, or , social media. just my choice.

---

### Post by mörgæs on 2020-04-15
Good, if the problem is solved then please mark the thread so.

---

### Post by oldfred on 2020-04-15
My first UEFI based build in 2014, I wanted to reuse power supply and case.
But it would not boot. Microcenter was nearby, so they (for a fee) put it on test bench & it immediately  booted. So they sold me new power supply. Regretted not getting new case as old one did not have USB or better now USB3 or USB-type C ports on front of case.

Second build was a SFF small form factor  build and pcpartpicker told me I was tying to fit a 3.5" HDD into a 2.5" drive space as SFF case is more like a laptop an sizes available. 
So I recommend pcpartpicker to verify build.

---

### Post by oneleded on 2020-04-17
> **mörgæs said:**
> Good, if the problem is solved then please mark the thread so.
thanks for the advice. i'm not done yet. i got a long way to go. i only have three components. i recently bought.
Ryzen 5 1600af, MSI Performance x470 Gaming Plus, Sabrent Rocket Q 1Tb., i got 2 RW drives. nothing else.
i got a long way to go. when i am done, i will mark it solved. its not fair to do anything other.
i still have unsolved threads. not many. it takes me forever, to solve a thread. i try though.

---

### Post by oneleded on 2020-04-17
> **oldfred said:**
> My first UEFI based build in 2014, I wanted to reuse power supply and case.
But it would not boot. Microcenter was nearby, so they (for a fee) put it on test bench & it immediately  booted. So they sold me new power supply. Regretted not getting new case as old one did not have USB or better now USB3 or USB-type C ports on front of case.

Second build was a SFF small form factor  build and pcpartpicker told me I was tying to fit a 3.5" HDD into a 2.5" drive space as SFF case is more like a laptop an sizes available. 
So I recommend pcpartpicker to verify build.
are there any better than pcpartpicker? i gather its better to get a correct PSU, an a case, to start with. then pay later. it was hard picking a MB, an im not sure i did. i'm stuck with it now. case's seem to be geared for gaming. another confusing factor for me. getting the correct power supply, even more so.
i think i will pass the $500 mark i set, not by much. if it go's 2 more hundred, it will still be a whopper of a PC . maybe not appreciated by some, but so...

---

### Post by CatKiller on 2020-04-17
All the components are standardised.

For the PSU there's one standard ATX size, and some smaller ones for smaller cases. You aren't getting a small case (because your motherboard is ATX) so you won't be getting a small power supply. That leaves your variables as capacity (wattage), quality/efficiency, and whether it's modular. PC Part Picker will tell you how much power your components will add up to, and the components will also give a recommended power supply capacity. Efficiency is how much of the input power is turned into output power rather than heat, and is colour coded. Modular power supplies make things a lot easier, since you just unplug the cables you aren't using rather than having them cluttering up the inside of the case. It tends to be a feature of the higher quality / more expensive PSUs rather than the cheapest possible ones. Generally, if you don't have a preference for which brand to go for (for example, because your choice of case includes a PSU), go for Seasonic.

Even though there's a massive range to choose from, cases are standardised too. You've got an ATX motherboard, so you're going to need a case that fits an ATX motherboard rather than one for the tiny motherboards. The relevant characteristic then is the balance between cooling and noise: open cases let the air in and the noise out. How much air and how much noise is then what's designed for. The rest is personal preference: what colour you want, whether you want a window or blinkenlights, and so on. My personal preference is to have lots of massive fans that barely spin at all, so that it doesn't make noise unless I definitely need the extra cooling, but mine's a high-end gaming rig that has a lot of heat to get rid of sometimes. Your cooling needs should be more modest.

---

### Post by oneleded on 2020-04-19
i dont have a preference for a case, an dont care for lighting, in or out, of the case. i'm going to be looking at the case. no one else much. just dont want much noise, and enough cooling to take care of the heat. i dont game, but some of my choices, require cooling.
since i'm trying to be a budget-builder,, my next look is at power supplies, that are dependable. case's seem to be the same, more or less, in what i'm looking for.
 i think i decided against a spinning 7200RPM HDD drive. for the price, i might as well go SSD. one more thing to cool down, though less noisy, in my PC, perhaps, or add a heat sink.
this basement, where its at, is only 62f in the summer. i got to wear x-tra clothes, to be here.

---

### Post by oneleded on 2020-04-22
i might have to spend a couple of x-tra bucks on case. thats not either here nor there yet. i want to get an inexpensive GDDR5. i got an MSI MB x470 Performance Gaming Plus Max. am i correct, in assuming, i dont need a special video card, or in other words, i dont have to match it to MSI?
i think it would be more important the match it to AMD Ryzen5 1600af, then match it to the MB. i also got an asus monitor, HDMI ready. its not much, but it suits me. MB is made in Taiwan. i dont know if that matters. Should i get a GDDR5 made else where? it seems like if Taiwan made GDDR5 cards, they be for MB's of
other Manufactures as well.

---

### Post by CatKiller on 2020-04-22
> **oneleded said:**
> am i correct, in assuming, i dont need a special video card, or in other words, i dont have to match it to MSI?

Again, standardised. You need *a* GPU, since your processor doesn't have its own, but it doesn't have to be a *special* GPU. PCI Express is the standard for attaching peripherals to your motherboard. It's on its fourth version now, but each version is backwards-compatible. 

You won't be buying GDDR5: that's for graphics cards. You might buy a graphics card that *has* GDDR5, but it's not a thing you buy yourself. You'll be buying DDR4 for your motherboard. Manufacturers generally provide a Qualified Vendors List, QVL, of which memory modules they've tested with a given motherboard model to make sure that they work properly.

---

### Post by oneleded on 2020-04-24
i'll be looking at the vendors list. thanks again.
i couldn't get access. part picker says the card i picked out works. EVGA Ge-Force GT 1030 SC 2GB GDDR5 Low Profile Graphic Cards 02G-P4-6333-KR 
i dont want to cause a bottleneck. this is what i have so far, and its my 1st from the ground up.
msi performance x470 gaming plus max
AMD ryzen 5 1600af
sabrent rocket Q1TB NVMe PCIe M2 2880 internal high performance SSD
crucial ballistix  3200MHz DDR4 DRAM 16GB(8GBx2) CL16
EVGA Ge-Force GT 1039 SC 2GB GDDR5 low profile 
i left out the RW drives, they are only important to me, and the case i get. i'm OK with USB also. i aint worried about sound system neither.
the graphics card is 64 bits instead of 128,, an scores low on some other points, but for what i'm looking for, i think it should work.
it has to be more that i got now. i just think i dont want the card to low, or to high, for the MB, or the ryzen 1600af.
i aint got much more to go to finish this project, what a journey. i cant say i enjoyed every minute of it, but i would gladly, do it again.
now for the power supply. most i've looked at, say they are missing, a 12v volt to motherboard connector, in case i want to overclock , or need more graphic, if i do some things, like rendering or illustration for example.
any way, the MB supposedly needs this extra 12v and is a 4 connector from the PSU.
PSU, i know not much about, except its better to have more power that not enough. a power supply can make or break your MB, and it will only use the power when needed.  i'm still learning. when i try to access MSI's site, i get problems finding out anything. There should be a QVL list of compatible PSU to match the MB.
say it aint so, and i will quit trying. now i got to depend on PCPartPicker, which, i think may be limited to possibilities of finding PSU.
maybe, i didnt set PCPartPicker right in the search, so it didnt have the chance.

---

### Post by oneleded on 2020-05-05
i listed my parts, except for the 2 RW drives. i get stuck on the power supply. i dont know how to due the proper search. the MB say's i need a special plug from the power supply, to supply 12 volts to the MB. [in case i need it]. i dont know how to due the search. the MB, is ATX, and their is a list of searches on pcpartpicker.com
should i leave my search to just ATX. not the other searches.

---

### Post by CatKiller on 2020-05-05
With the power supply, as I said upthread: if you don't know which to go for, go for Seasonic. They're quality power supplies and should have everything you need. There's also a calculator on their website to estimate what capacity you should look for.

---

### Post by oneleded on 2020-05-07
Thanks for you help. it seems parts are in short supply everywhere. i got only got to buy a PSU, an a case. then i'm done. the PSU slows me down, because of an additional 12v to the MB. [in case i need it]. ten year's down the line, maybe. every PSU i've found that is compatible is "out of stock" with my MB. maybe case's will be, for i get done. i just got bad timing, to buy. i'll check up thread, an i better hurry, on the part picker or, calculator part, at sites. 550w is plenty, at most places i've seen. even some sites that say, i dont need the additional 12v to the MB. just a marketing ploy thing by MSI. who knows what to believe anymore.
linux rings true, has good people. best quit, while i'm ahead. ;~}

---

### Post by CatKiller on 2020-05-07
I'm pretty sure the power connectors to the motherboard are standard. As I recall, there's a big connector that ATX motherboards have had for decades (since the introducing of ATX), and a supplemental one (that I think is called EPS) for processors that need more power. Processors started needing more power in the Pentium 4 era, so all (maybe only most) PSUs should have that connector too, AFAIK. 

> **oneleded said:**
> i just got bad timing, to buy.

I was in the same boat. My old (semi-retired) Sandy Bridge, as it turned out, was too long in the tooth for folding coronavirus proteins and died, and the coronavirus had disrupted all the supply chains. They did pick up again, though, and the parts arrived a few days ago.

---

### Post by oneleded on 2020-05-07
that's funny in a way, i know what "long in the tooth means" + the virus, that just happened out of nowhere. ya left out short on hair, if ya got any, an grey or white hair. haha
i'm well past a receding hair line, it goes to the back of my head. Oh Well!!
shiny skin reflects sunlight, an my head does also.

---

### Post by oneleded on 2020-05-15
i'm just waiting on a case an power supply., then put it together.. my list
$132 MSI x470 gaming plus max
$137 Sabrent Rocket Q 1TB M.2-2280 NVMe
$135 Supernova 80+Gold 650w full mod.
$ 80 Crucial 16GB(2x8) DDR4 3200 
$ 94.oo Be Quite 600 Pure Base mid tower
$90.oo Ryzen 5 1600af
$100. EVGA GeForce 1030 GDDr5 [i might get into a little rendering later on]
$768.oo  total.  

i have 2 RW drives already, that i will add. $ 50.oo  my budget was $500. prices have when up a bit due to the virus i think, parts were limited a bit also, maybe a touch of price gouging.  this is the longest shopping trip i ever went on. shipping and taxes are added in the price. i want to thank you for your help in this matter, i sure needed it.
its be fun and aggravating at the same time, plus i learned a few things.  //ed
i forgot to add, i still have put it all together and i might have to start a new post. lets hope not.

---

### Post by oneleded on 2020-05-15
> **CatKiller said:**
> The Ryzens are great. I'm not sure why you'd pick the 1600, though, rather than the newer models. They've had some big improvements as they've developed. 

Knowing which processor you're going with gets you most of the way to knowing which motherboard; there are only a handful of chipsets to choose from, and then it's picking a manufacturer that you find reputable and balancing which features you want against how much you want to spend. The choice of motherboard determines what type of RAM you need. PC Part Picker is a useful tool: it will remember where you got to on selecting parts and will highlight any incompatibilities. For RAM specifically each motherboard will have a QVL of modules that have been tested and shown to work properly. 

I'd recommend 16 GB to everyone in a new build, unless they have a particular need for 32 GB. There's not really a reason to have less these days, particularly if you're aiming for longevity.
the 1600af 12nm is different than the 1600ae 14nm. its closer to 2600 ryzen, or was it 2500 ryzen.

---

### Post by oneleded on 2020-06-13
my power supply disappeared. it was unexpected. i have looked everywhere. i dont think i lost it, or misplaced it. so, i cant let you know how it worked out.
and i was planning too. i ordered another one. not too much choice. it should be a week or so, if it is.
 its still hard to get parts, since corona.
i was going to use inappropriate words, lets just say, im not a happy camper. i would, and have, kept my parts, in my new build, on my shelve, since this started.
i cant see anyway, that i would have lost this. i have built a decent machine, for the price, during a shortage of parts.  ed

still waiting, i cant believe its only, been a week. it feels like a month.

---

### Post by oneleded on 2020-07-15
i finally got the power supply, in the meantime, i forget what i wrote. i still got the jest of it.

---

### Post by oneleded on 2020-07-22
always, another question: the user guide tells you how to hook up the wires. by the times i look at it in the user book, then look at the board, i forget. i'm gonna had to make drawings. that will take me a lot of time too. has someone already posted something like this? my short term memory dont work right, nor does my short sight. i wouldnt ask if it was wasnt necessary.

---

### Post by CatKiller on 2020-07-22
Just take your time.

Sketches are a good idea. A surface to work on with lots of light helps, too.

You'll have connections from the case to the motherboard, data connections to any drives, power to motherboard and CPU, power to drives and potentially to the graphics card.

---

### Post by oneleded on 2020-07-24
thanks; the little single connectors at the bottom of the board kinda had me worried. i already had my sketch paper lined out, working on lights, i guess i was just looking for a shortcut. needed a push

---

### Post by CatKiller on 2020-07-24
I'm guessing by that description that you mean the connections from the case to the motherboard for LEDs, the power switch, and so on. Yes, they can be fiddly. Some motherboards have a connector block that you can use: you plug them into the right places in the block, and then plug the block into the motherboard.

---

### Post by kurt18947 on 2020-07-25
My last build I installed and connected as much as I could before mounting the motherboard to the case. I find the front panel connectors - power, reset HD LED connector the most fiddly. They're somewhat easier if I don't have to work down in the case. I've downloaded the motherboard book PDF, found the page with the connectors, did a screen shot then enlarged it so I could read the type. I'm sure most 20 somethings don't need to do that, I haven't had 20 something eyes for  30 something years.

---

### Post by oldfred on 2020-07-25
+1 on Kurt18947's suggestion.

I installed motherboard on new build using old power supply that should have been new enough & worked on older system.
But system would not boot at all. Took to Micocenter store & they ran on tech bench with their power supply & monitor. It worked. So new power supply.

But tech suggested to put motherboard carton on top of case as insulator,  and motherboard on top of carton. Then connect essential connections to test if it boots. Lot easier than putting & & taking out all the screws that are hard to get to.

---

### Post by oneleded on 2020-08-02
starting a new thread, got every thing together. i should show ya a picture. ya have been of much help.
there are some more pictures, but this will do. it's really quite.

---

### Post by oneleded on 2021-02-06
Well, just to let ya know, i am running, an got two OS on the SSD. i am grateful for the help. i couldnt done it without the help.

---

