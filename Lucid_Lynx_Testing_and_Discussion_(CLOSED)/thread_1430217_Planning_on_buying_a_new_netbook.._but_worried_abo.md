---
title: "Planning on buying a new netbook.. but worried about this GMA500 issue"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by alexcckll on 2010-03-15
Hi folks, 

I'm planning on buying a new netbook after Lucid is released, but am worried that with this Intel GMA500 issue - what netbooks are good to run?

Can anyone give advice on what netbooks should Just Work with Lucid when it goes production?

Also - would there be plans to SRU Intel's new drivers if the new Moorestown stuff comes in around a point release?

[http://www.phoronix.com/scan.php?page=news_item&px=NzY2MA](http://www.phoronix.com/scan.php?page=news_item&px=NzY2MA) - one news article...

I'm worried about spending money on kit when it may not be supported... or if a kernel update would break things if I buy preinstalled from Linux Emporium.

Oh - and iPlayer at a decent resolution would be a main requirement...

---

### Post by ssam on 2010-03-15
i got my S12 from linux emporium, and it works fine with lucid.

the only issue is with the broadcom wireless chip. broadcom wont allow anyone to distribute the firmware, so you need to download it over a wire when you install a new ubuntu. also the opensource driver for the chip is broken on some BIOSs ( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502433](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502433) ), so you need to used the proprietary one (system->admin->hardwaredrivers).

i think the gma500 has gone out of fashion. it shouldn't be too had to find which graphics card a netbook has.

---

### Post by Seventh Reign on 2010-03-15
The real problem is whichever netbook you get for LL-10.04 will most likely be broken by MM-10.10.

---

### Post by cmccauley on 2010-03-15
You can get the GM500 to work well with Karmic and Lucid but really it is an unloved chipset. I have my Dell Mini 10 running nicely with Karmic but I really wanted to run Moblin and that option is shut off now.

Save yourself the bother, keep your options open and just buy something with an alternative video adapter.



Chris

---

### Post by snowpine on 2010-03-15
Intel 945G graphics card is low cost and well supported by Linux (and probably always will be).

---

### Post by andrewabc on 2010-03-15
Stay away from GMA 500
GMA950 is old.

There are new netbooks out now that use NM10 chipset and are only $20-$50 more.

You would want n450 processor (which has nm10 chipset and gma3150 graphics.)
The nm10 chipset uses a lot less power than gma950 and is also a bit faster graphics wise (no games or 1080p, but better than gma950 for basic tasks).

[here](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2034940772%201722253889&name=N450%281.66GHz%29) is list of n450 netbooks at newegg (similar stuff can be found at any other store).
There are more new n450 (gma3150) than n270+n280 (gma950) together. You won't see any new gma950 products now. Old stock will probably be on good sales to get rid of inventory since new chipset is preferred (in a couple months).

[Intel Atom D510: Pine Trail Boosts Performance, Cuts Power](http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=3692&p=1)
here is the benchmarks to prove that nm10 is much better than gma950. benchmarks use dual core processor. So speed wise n450 is a bit faster but power wise it is a lot better.

[Table of GMA graphics core](http://en.wikipedia.org/wiki/Intel_GMA#Table_of_GMA_graphics_core)

Basically the biggest thing about NM10 over gma950 is that it uses [1/2 the power](http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=3692&p=11). So longer battery life, probably less heat. Similar performance. Gotta love the pentium 4 power usage. That's why I replaced old P4 desktop with eee box n270. 10% of the power usage.

---

### Post by meborc on 2010-03-15
> **andrewabc said:**
> Stay away from GMA 500
GMA950 is old.

There are new netbooks out now that use NM10 chipset and are only $20-$50 more.

You would want n450 processor (which has nm10 chipset and gma3150 graphics.)
The nm10 chipset uses a lot less power than gma950 and is also a bit faster graphics wise (no games or 1080p, but better than gma950 for basic tasks).

[here](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2034940772%201722253889&name=N450%281.66GHz%29) is list of n450 netbooks at newegg.
There are more new n450 (gma3150) than n270+n280 (gma950) together. You won't see any new gma950 products now. Old stock will probably be on good sales to get rid of inventory since new chipset is preferred (in a couple months).

[Intel Atom D510: Pine Trail Boosts Performance, Cuts Power](http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=3692&p=1)
here is the benchmarks to prove that nm10 is much better than gma950. benchmarks use dual core processor. So speed wise n450 is a bit faster but power wise it is a lot better.

[Table of GMA graphics core](http://en.wikipedia.org/wiki/Intel_GMA#Table_of_GMA_graphics_core)

Basically the biggest thing about NM10 over gma950 is that it uses [1/2 the power](http://www.anandtech.com/cpuchipsets/showdoc.aspx?i=3692&p=11). So longer battery life, probably less heat. Similar performance. Gotta love the pentium 4 power usage. That's why I replaced old P4 desktop with eee box n270. 10% of the power usage.

wow, there's some good information :D thanks...

---

### Post by snowpine on 2010-03-15
Cool links and good info Andrew! How is Ubuntu support for this new chipset?

---

### Post by andrewabc on 2010-03-15
> **snowpine said:**
> Cool links and good info Andrew! How is Ubuntu support for this new chipset?

No idea since I don't have one.

My desktop is early core2duo with intel G965chipset and GMAx3000 and works fine. So I presume the gma3150 (which is based on GMA3100) should work fine.

Hopefully someone does a review somewhere with the new processor/ubuntu.
quick googleing found someone did install ubuntu to n450 processor.
[Installing Ubuntu on a new Acer Aspire One N450](http://fnielsen.posterous.com/installing-ubuntu-on-a-new-acer-aspire-one-n4) ->good review

The n450 for netbooks has been out since early January, although only had big presence at retailers (for decent price) since February. atom n270/280 +GMA950 is finally dead. :P

EDIT:
[AO532h (N450-GMA3150-1GB-HDD160GB-Atheros B&G-BT)](https://help.ubuntu.com/community/AspireOne/Ubuntu9.10#AO532h%20%28N450-GMA3150-1GB-HDD160GB-Atheros%20B&G-BT%29)

[1005PE 64 bit Graphics drivers (and where to find all the x64 drivers)](http://forum.eeeuser.com/viewtopic.php?id=82496)

Also very important is the n450 processor is 64bit capable. n270/280 is not.
[List of Intel Atom microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Atom_microprocessors)

with new NM10 chipset, upcoming nvidia ion2 will be supported. So you have normal GMA3150 for basic tasks (good battery), and when you need to play a game or 720/1080p nvidia will kick in.
[NVIDIA's Next Generation ION Announced, Optimus + a 16-core Version](http://www.anandtech.com/mobile/showdoc.aspx?i=3754)
> The Next Generation ION (NG-ION) platform consists of a Pineview netbook with a discrete graphics chip from NVIDIA, with Optimus allowing the GPU to switch on/off as needed. Note that there is no Optimus technology for nettop solutions, which will simply use an NVIDIA discrete GPU all the time. On a nettop that's always plugged in, NG-ION might use ~3W more power at idle, but that's not enough to worry about. There's also a benefit to just keeping things simple by using a standard discrete GPU.
Obviously will cost a bit more than regular gma3150 netbook. By 2011 dualcore atom + nvidia ions will be the new norm. Already selling one, but costs [$500](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220659)

---

### Post by andrewabc on 2010-03-17
Review for [Asus eeepc 1001](http://www.anandtech.com/mobile/showdoc.aspx?i=3770) netbook.

Stay away from gma950 or gma500 netbooks. :)
Unless you need absolute cheapest netbook.

When choosing NM10 netbooks be careful as some models only have wireless b/g (usually cheapest ones).

---

### Post by VMC on 2010-03-17
> **andrewabc said:**
> Stay away from GMA 500
GMA950 is old.

.... That's why I replaced old P4 desktop with eee box n270. 10% of the power usage.
good information there, I'm especially interested in the P4 comment, as I have a Dell with a P4. How does it compare speed wise for you. I don't need benchmarks just your view of the overall speed differences, and "feel". Much improved, or about the same.  Thanks.

---

### Post by andrewabc on 2010-03-17
> **VMC said:**
> good information there, I'm especially interested in the P4 comment, as I have a Dell with a P4. How does it compare speed wise for you. I don't need benchmarks just your view of the overall speed differences, and "feel". Much improved, or about the same.  Thanks.

ok, here's basic specs of my old P4.
pentium4 1.7ghz
Intel i845 chipset (ICH2!!!!)
Nvidia Corp RIVA TNT2 Model 64 [NVM64]
80gb hard disk 2mb cache.
cdrom burner
dvd rom
3x256mb SDR ram
USB 1.1 (can't liveusb boot on this computer)

So cheapest eeebox beats pretty much every aspect speed wise.
[here](http://www.newegg.ca/Product/Product.aspx?Item=N82E16883220012) is exact product/place I bought. They have others identical selling at most online places (newegg USA sells for $220 free shipping linux version). acer revos are same price for better performance (nvidia ion).

atom 1.6ghz ->0.1ghz  slower than P4. But uses MUCH less power/heat/noise, probably better processor architecture too.
intel 945 chipset (GMA950). MUCH better chipset. ICH7
GMA950 faster than nvidia tnt2.
160gb ->twice hard drive size. eeebox uses SATAII. old pentium 4 uses IDE. Not sure on cache probably 8 or 16mb (will replace with SSD in future when good 30gb SSD drop to <$100) Hard drive is probably weak point, same as with netbooks that ship with shitty drives. But really easy to replace with SSD in future (unlike netbooks).
no optical drives ->less power needed. smaller size allowed.
1gb DDR2 ram. Much faster than 768mb SDR ram (so it goes SDR RAM -> DDR RAM ->DDR2). If you can get [firefox profile to run in ram](http://ubuntuforums.org/showthread.php?t=1120475) and be stable, you'd bypass the slow hard drive (aka hard drive thrashing in firefox as shown on any HDD based computer (don't get this problem on SSD)).
USB 2.0. omg so much faster than 1.1

Now that hardware spec comparison over.
eeebox (or any nettop) is small. Hold in one hand easy (bit heavy) to move around if needed. ~size of nintendo wii if you have no idea (or get out ruler/paper and draw size using dimensions given). P4 real heavy... My P4 computer uses around 250 watts according to some watt programs. [power wattage calculator](http://www.3dcool.com/PWC.php) and [antec power supply calculator](http://www.antec.outervision.com/index.jsp)->says 225 watts when I fill it out.
eeebox uses 22 watts regular use, 25 watts max (acer revo uses ~30-50 watts because of ion and dual core).

[Asus Eee Box B202: An Atom-based mini PC](http://www.silentpcreview.com/Asus_EeeBox_B202)
review specializes in sound and wattage. Verdict: awesome.

I can't hear any sound from eeebox unless I put my head up next to it (1 foot). My old P4 was real loud (bad fans?) and basically had to turn up TV volume in same room to compensate, although most old computers are like that. So using 10% electricity, and extremely quiet are nice.

As for speed wise feelings. It is only a bit faster than P4. Doing stuff seems smoother (not as much lag). In P4 there would sometimes be lag even when program (firefox) open and doing browsing stuff. eeebox doesn't lag as much. USB2.0 makes transferring files much better. Built in wifi so no need to have usb wireless device plugged in (as was needed in P4).
eeebox can attach to back of vesa monitors, so if you want compact it is possible. Since it uses SATA II and 2.5" hard drive, if you want more speed you can
1. add another 1gb laptop ram (2gb max)
2. Once good 30gb SSD get dirt cheap replace original slow hard drive. Make better web browsing machine.

If you want cheapest device possible to replace old P4, the eeebox B202 is great, and good for a desktop web browsing device. I figure it will pay for itself with electrical savings over 3 years (no evidence, but if uses 10% power and runs 6 hours per day every day...). I live in 100 year old house so using less electricity also improves safety.

If you want to spend $100 more ($330 in Canada) you can get [Acer Revo](http://www.newegg.com/Product/Product.aspx?Item=N82E16883103235) which has dual core atom and nvidia ion (1080p playback), HDMI, 2gb ram, win7 home premium etc. More futureproof. There is also 4gb ram model for $400.

If you use your dell P4 often (depends on exact hardware and uses), I'd definitely replace it with eee box B202 or [acer revo AR1600-U910H](http://www.newegg.com/Product/Product.aspx?Item=N82E16883103228) (cheapest models), or if want more futureproof (hook up to tv for HTPC, light gaming) get the better acer revo. Save some money, do research on products and wait for a sale. Make sure the device will do exactly what you want it to do. Only want web browser/light tasks and ubuntu? B202 or cheap acer revo. Want more futureproof and faster? Newer acer revo (and eee box once they get their **** together, currently wayyyy overpriced for ion model). You'll love getting rid of old desktop computer.

I'd say we're at the point where nettops are cheaper to buy than putting up with shortcomings of old P4 computers and in the end probably cost neutral due to power savings (power savings and more efficient offset purchase price). I waited 9 months before buying eeebox as I waited for price drop (Bought in early January 2010, then I found out about acer revo awesomeness couple weeks ago). new acer revos are pretty much faster than my 3.5 year old core2duo computer at 1/2 the price I originally paid for it (mostly video card is 3 times faster than my GMA965 x3000). So by end of year prices should drop more for higher end nettops.

I paid $1000 for just my P4 desktop in 2002. Now for 1/4 the price I can get slightly faster (I'd term it more efficient with the tech advances, not a lot faster), much smaller, 10% power usage, silent computer. If you're looking for pure speed improvements, eeebox B202 won't help, but if you are somewhat happy with your P4 performance and just want an updated computer that is much more efficient in every way, then it is the way to go (assuming old P4 machine like mine).

If you absolutely need DVD drive bundled, you can get expensive version of eeebox [here](http://www.newegg.com/Product/Product.aspx?Item=N82E16883220023). But I'd say overpriced. Give it until end of year.

Feel free to ask any other specific questions.

EDIT:
It should be noted this nettop my parents use not me (other than updating/troubleshooting/testing). So they're slow with computers so speed doesn't matter (firefox used 99% of time and works great), and the mains reasons I got it was because of 10% power/silent/less heat/efficient and also important: Less ugly than big P4 tower. P4 tower was on floor, nettop is on desk behind monitor (not hooked onto monitor though) Hooked up is 3.5 year old 20" LCD that still works great.

Also note if you use or think of using UPS (Uninterruptible power supply) because your power goes off/on during storms or regular use, these nettops would work better. Less electricity needed, last longer/more time to properly shutdown. Combine with newer LED LCD monitors and should be good solution.

EDIT:
If the Dell P4 is your main computer, I'd upgrade to dual core atom + nvidia ion nettop. If it is secondary or compliments a laptop, then single core atom should suffice.

---

### Post by garba on 2010-03-17
As many other fellow ubuntu users have already pointed out, save yourself the trouble and stay away from this crappy thing that goes by the name of GMA500. I bought an Asus 1101HA back in November, it's a lovely, neat lappy which can run Windows 7 flawlessly, but linux support is nearly non-existant, it's ridicolous how poorly unsupported this chipset is. This is 10 years old technology but still the manufacturer refuses to disclose any information which could be useful for the community to develop open source drivers. They provide a binary blob though, but as soon as either the kernel or xorg are updated you will be out of luck. It's Intel we have to say thanks to: they licensed this "technology" from powerVR but they just can't seem to bother with providing half-decent support for this thing. Not bad for a company who claims to be seriously committed to open source technology. Bottom line: do yourself a favor and stay away from this chipset if you want to run linux on it.

---

### Post by VMC on 2010-03-17
> **andrewabc said:**
> ok, here's basic specs of my old P4.
pentium4 1.7ghz
Intel i845 chipset (ICH2!!!!)
Nvidia Corp RIVA TNT2 Model 64 [NVM64]
80gb hard disk 2mb cache.
cdrom burner
dvd rom
3x256mb SDR ram
USB 1.1 (can't liveusb boot on this computer)
...

Thanks for the information. I forgot to say I have a 2.6 gHz P4, USB2, so the comparison wouldn't be the same. I have read a review of dual-core Atom and P4 using my gHz speed and P4 beat in most categories.

I'm thinking of of also getting a new computer and leaning towards 64-bit for better video processing. The Atom chip does look very interesting for netbooks though.

---

### Post by andrewabc on 2010-03-17
> **VMC said:**
> Thanks for the information. I forgot to say I have a 2.6 gHz P4, USB2, so the comparison wouldn't be the same. I have read a review of dual-core Atom and P4 using my gHz speed and P4 beat in most categories.

I'm thinking of of also getting a new computer and leaning towards 64-bit for better video processing. The Atom chip does look very interesting for netbooks though.

Dual core atom has 64 bit support. Although doubt good for video processing :P

Yeah, you're dell P4 is a lot faster than mine. So wouldn't get speed improvements. Just the low power/heat/noise/small size benefits.

If you're buying a primary computer a traditional desktop would be best speed/$.
I'm trying to wait until end of year to get SATA6.0 and usb 3.0. Either that or acer revo (or similar nettop) 4gb model when price drops a lot.

---

### Post by 3rdalbum on 2010-03-17
The Acer Aspire One D250 dual-boots Windows and Android, and doesn't have any problems with Ubuntu 10.04 apart from "Compiz Blur plugin doesn't work". It's an older Atom and GMA950, but it should be fairly inexpensive. And let's face it, you don't need much in the way of graphics acceleration on a netbook.

---

