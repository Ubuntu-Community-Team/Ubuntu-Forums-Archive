---
title: "Upgrade 11.04 to 11.11 with usb-media"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2011-11-03
I I wonder how I can upgrade by adding a usb-stick with a 11.11 on. It's boot and I can run live, but I the Update manage are only able to add CD/DVD-media.

---

### Post by zvacet on 2011-11-04
If you have 11.10 on usb then just boot from it and you should see option for upgrade.

---

### Post by PfromD on 2011-11-04
I'm facing sort of the same problem. I hadn't noticed that we're up to v.11 .. and why haven't ubuntu advised med of this it self? (using lucid lynx)
I then downloaded the latest and made a usb through unetbootin, but it doesn't work as i imagined it would. it doesn't boot up in ubuntu, neither in live or directly install/upgrade mode but in some weird unetbootin mode I've never seen before ... AAARGGHH, help :)

---

### Post by zvacet on 2011-11-04
@ **PfromD**

You can not skip releases.If you want to install 11.10 then back up your home partition ( and etc I suppose).I will wait until 12.04 is released and then do direct upgrade from LTS>LTS.

---

### Post by raja.genupula on 2011-11-04
> **PfromD said:**
> I'm facing sort of the same problem. I hadn't noticed that we're up to v.11 .. and why haven't ubuntu advised med of this it self? (using lucid lynx)
I then downloaded the latest and made a usb through unetbootin, but it doesn't work as i imagined it would. it doesn't boot up in ubuntu, neither in live or directly install/upgrade mode but in some weird unetbootin mode I've never seen before ... AAARGGHH, help :)

Hi , Ubuntu itself have a startup disk creator , i always use that and upto now it wasnt failed me .are you sure about BIOS settings first priority is USB Live.try to do with any other USB(may be this one have problem) and check the checksum of ISO.

---

### Post by searchfgold6789 on 2011-11-04
> **PfromD said:**
> I'm facing sort of the same problem. I hadn't noticed that we're up to v.11 .. and why haven't ubuntu advised med of this it self? (using lucid lynx)
I then downloaded the latest and made a usb through unetbootin, but it doesn't work as i imagined it would. it doesn't boot up in ubuntu, neither in live or directly install/upgrade mode but in some weird unetbootin mode I've never seen before ... AAARGGHH, help :)
Yeah, I stopped trusting UNetbootin; it used to do that to me all the time... Try the default USB disk creator in Ubuntu, you'll find it to work much better. Fortunately it seems as if your BIOS settings are indeed correct; it's not completely skipping the USB, but rather booting from it and not displaying a correct boot menu (the contents of the bootloader on the USB need to be replaced with something more valid).

---

### Post by Azyx on 2011-11-04
> **zvacet said:**
> If you have 11.10 on usb then just boot from it and you should see option for upgrade.

I was unclear. Sorry. The problem was that i didnt could boot from usb  on the machine (Bad BIOS), but want to have it in repository The usb-disk work, cos I have used it on other machines.

---

### Post by Azyx on 2011-11-05
> **searchfgold6789 said:**
> Yeah, I stopped trusting UNetbootin; it used to do that to me all the time... Try the default USB disk creator in Ubuntu, you'll find it to work much better. Fortunately it seems as if your BIOS settings are indeed correct; it's not completely skipping the USB, but rather booting from it and not displaying a correct boot menu (the contents of the bootloader on the USB need to be replaced with something more valid).

That UNetbootin doesn't work, may it depend on that Ubuntu use another blocksize than other distrubitions? 4M instead of 1M, or vise versa?

---

### Post by zvacet on 2011-11-05
Read [this.]("http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid")

---

### Post by PfromD on 2011-11-05
> **zvacet said:**
> @ **PfromD**

You can not skip releases.If you want to install 11.10 then back up your home partition ( and etc I suppose).I will wait until 12.04 is released and then do direct upgrade from LTS>LTS.

How is 10.04 > 11.11 skipping a release?? and am I to understand that once 12.04 is released it will inform me and suggest the update on its own, done 'diskless' or will I need to create a disk for that. Or in my case an updated USB (cd drive doesn't work anymore)

---

### Post by Azyx on 2011-11-05
> **PfromD said:**
> How is 10.04 > 11.11 skipping a release?? and am I to understand that once 12.04 is released it will inform me and suggest the update on its own, done 'diskless' or will I need to create a disk for that. Or in my case an updated USB (cd drive doesn't work anymore)

After 10.04LTS are 10.10 and 11.04 before 11.10. You can upgrade 10.04 LTS to 12.04 LTS i think, but they have special upgrade-tool for LTS realeses

---

### Post by zvacet on 2011-11-05
Nothing special about upgrade LTS releases.You can use synaptic to do that when time come.

---

### Post by Azyx on 2011-11-05
> **zvacet said:**
> Nothing special about upgrade LTS releases.You can use synaptic to do that when time come.

Yes, but you can not uppgrade 10.04LTS to 11.11 directly!!! you must fist upgrade to 10.10, then 11.04 and then 11.11. But if you have 10.04 LTS you can upgrade directly to 12.04, I think, anyway it was so for 8.04LTS to 10.04LTS.

---

### Post by zvacet on 2011-11-06
@ **Azyx**

Yes, I know upgrade must go from one releases to another without skipping.I told OP that in my previous post.

---

### Post by Azyx on 2011-11-06
> **zvacet said:**
> @ **Azyx**

Yes, I know upgrade must go from one releases to another without skipping.I told OP that in my previous post.

But  **PfromD** didn't understand what you mean I think?

---

### Post by PfromD on 2011-11-06
I've made a USB stick with the build in tool in 10.04, and actually it DOES -by the looks of it- allow me to upgrade from 10.04 to 11.10.
Haven't tried it out yet though because of zvacet's comment about his own plan to wait it out until 12.04 (but when IS that??)
But when running it as a live OS 11.04 almost looks like a totally new OS.
Oh boy it looks neat :) If Ubuntu was a girl I'd have to admit to being in love ;-)

---

### Post by PfromD on 2011-11-06
By the way .. why the F.. does the overview tell that I'm on gutsy gibbon when I'm on lucid lynx, and in my 'user CP' I'm apparently not able to edit this info because I haven't got enough posts. Weird and annoying!

---

### Post by Azyx on 2011-11-06
> **PfromD said:**
> I've made a USB stick with the build in tool in 10.04, and actually it DOES -by the looks of it- allow me to upgrade from 10.04 to 11.10.
Haven't tried it out yet though because of zvacet's comment about his own plan to wait it out until 12.04 (but when IS that??)
But when running it as a live OS 11.04 almost looks like a totally new OS.
Oh boy it looks neat :) If Ubuntu was a girl I'd have to admit to being in love ;-)

The version number are year and monts so next year (2012) in april. I don't like Unity so I have installed 'gnome-session-fallback':

```
sudo apt-get install gnome-session-fallback

```

There you have panels and stuff that you can control. Some things differ, for instance to add things to the panel, like you have to press alt-key before right-click.

/Cheers

---

### Post by PfromD on 2011-11-06
Is unity what they call the panel on the left side or the cloud service?
I think the new panel on the left looks real nice, but as I said I've so far only glanced at 11.10. Don't know how it handles in the long run.

---

### Post by Azyx on 2011-11-06
> **PfromD said:**
> Is unity what they call the panel on the left side or the cloud service?
I think the new panel on the left looks real nice, but as I said I've so far only glanced at 11.10. Don't know how it handles in the long run.

It is  the launcher on the left side. It just launch applications, not for instanse show clock, system monitoring or other apps as the gnomer-panel or a dock.

---

### Post by zvacet on 2011-11-06
@ **Azyx**

> I've made a USB stick with the build in tool in 10.04, and actually it DOES -by the looks of it- allow me to upgrade from 10.04 to 11.10.

That iso you put on usb doesn´t allow you to do upgrade.If you use it it will be fresh install,meaning that all your files will be deleted if you didn´t store them somewhere alse (external hdd or something similar).Now I will try to explain as far as I can about upgrades and ubuntu release sign.
Your release is made in  2010 April so you run 10.04 (short from 2010 04).That is **L**ong**T**erm**S**upport.Read [this.]("https://wiki.ubuntu.com/LTS")

If you want to upgrade from 10.04 to 11.10 you will have to do this:

10.04>10.10>11.04>11.10

Above is way how you upgrade normal releases.In your case is time and bandwight consuming with no guarantee that will be successful.Second way is to upgrade from one LTS to another.In your case it is 10.04>12.04.

---

### Post by Azyx on 2011-11-06
> **zvacet said:**
> @ **Azyx**

That iso you put on usb doesn´t allow you to do upgrade.If you use it it will be fresh install,meaning that all your files will be deleted if you didn´t store them somewhere alse (external hdd or something similar).Now I will try to explain as far as I can about upgrades and ubuntu release sign.
Your release is made in  2010 April so you run 10.04 (short from 2010 04).That is **L**ong**T**erm**S**upport.Read [this.]("https://wiki.ubuntu.com/LTS")

If you want to upgrade from 10.04 to 11.10 you will have to do this:

10.04>10.10>11.04>11.10

Above is way how you upgrade normal releases.In your case is time and bandwight consuming with no guarantee that will be successful.Second way is to upgrade from one LTS to another.In your case it is 10.04>12.04.


It's not my quote, it's PfromD.

---

### Post by zvacet on 2011-11-07
@ **Azyx**

Sorry,my mistake.But OP should read that my response to that quote.

---

### Post by PfromD on 2011-11-08
[QUOTE=zvacet;11432724]@ **Azyx**



That iso you put on usb doesn´t allow you to do upgrade...QUOTE]

Ok, but are LTS releases then biannual since I haven't been informed of any major updates here in '11?
|
|
never mind. I asked before reading the above link.

---

### Post by Azyx on 2011-11-08
> **PfromD said:**
> [QUOTE=zvacet;11432724]@ **Azyx**



That iso you put on usb doesn´t allow you to do upgrade...QUOTE]

Ok, but are LTS releases then biannual since I haven't been informed of any major updates here in '11?

yes they are biannual. 6.04, 8.04, 10.04, 12.04 and so on. LTS are more stable.
I talked about that my computer did not allow to boot from usb, and when I should upgrade with upgrademanager it's could only allow CD/DVD-media (not ISO on the harddrive or usb-media) So I had to download all files to make an upgrade. I have a very slow internet-connection, so it take a couple of hours.

It is like someone here also sai. Upgrade goes from disto till distro(half-year) and LTS till LTS (biannual).

---

