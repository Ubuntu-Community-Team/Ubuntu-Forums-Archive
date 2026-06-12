---
title: "Upgrading from 8.4.1 to 8.10"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by poldie on 2008-10-29
I've never done a release upgrade before.  I want to upgrade tomorrow and am wondering what sort of problems I might expect.  If I've hand edited configuration files, such as to get my Acer Aspire one wifi working, will they be overwritten with new ones, or left untouched.  If the latter, what if configuration files need to be updated for 8.10 apps/features to work. 

I have two installations - the Acer one, and my main desktop PC.  The latter is a regular PC without wifi.  I've upgraded some of the apps on it, such as OpenOffice and VLC.  Should I uninstall apps in preparation, or should I leave them?

Perhaps I worry too much, but I'm used to Windows, and in the past I've just wiped out the OS and installed the new one from scratch, but Linux seems to be much smoother in terms of installation/upgrades so I thought I'd give the regular updater a chance first.

Thanks for any help.

---

### Post by meindian523 on 2008-10-29
Actually,it's recommended to do a clean install rather than do a distribution upgrade.If you have a separate /home partition,your personal settings shall be saved,but any editing of config files(may / may not be required in the new version,after all the kernel is new and might support your Wifi etc out of the box),if required,will have to be redone.This is true whether you clean install or allow the updater to do it's job.

---

### Post by fikelfikel on 2008-10-29
> **poldie said:**
> I've never done a release upgrade before.  I want to upgrade tomorrow and am wondering what sort of problems I might expect.  If I've hand edited configuration files, such as to get my Acer Aspire one wifi working, will they be overwritten with new ones, or left untouched.  If the latter, what if configuration files need to be updated for 8.10 apps/features to work. 

I have two installations - the Acer one, and my main desktop PC.  The latter is a regular PC without wifi.  I've upgraded some of the apps on it, such as OpenOffice and VLC.  Should I uninstall apps in preparation, or should I leave them?

Perhaps I worry too much, but I'm used to Windows, and in the past I've just wiped out the OS and installed the new one from scratch, but Linux seems to be much smoother in terms of installation/upgrades so I thought I'd give the regular updater a chance first.

Thanks for any help.

Hi. I'm also upgrading to 8.10 from 8.04.1 tomorrow, with an Acer Aspire T660 Desktop. I've never upgraded before either, I'm a newbie to Linux. However, I don't think the upgrading of OpenOffice should do any harm. Your WiFi should be left alone, ifact, everything should be left alone, like your files, folders.

If your WiFi don't work, could you please tell us your specs? I think it might take a day or two for the upgrading of apps, but some of them should remain untouched.

---

### Post by tuxxy on 2008-10-29
I had hardly any issue with updating to Ibex, to update press ALT + F2 and enter

```
update-manager -d
```

Then you should see the option for dist upgrade :)

---

### Post by mthei on 2008-10-29
Upgrades are actually pretty solid with Ubuntu. You may not get all the new features (correct me if I'm wrong), but you'll still get all the newer versions of your installed packages.. However, I wouldn't recommended upgrading tomorrow, though, as a) the servers will probably be insanely busy (depending on your mirror, of course) and b) it's better to wait at least one week for the heavier bugs to get worked out, at least in my experience.

---

### Post by meindian523 on 2008-10-29
tuxxy:
Do you have the same configuration as the OP?

---

### Post by Sef on 2008-10-29
Before upgrading or clean installing, **back up** your **data**.  There are no guarantees that all will go well.

---

### Post by Jammy4041 on 2008-10-29
I would do a clean install, and would wait until next week to actually upgrade. If you are on hardy heron, go to the software sources, click on the update tab, under release upgrades make sure "normal releases" shows. 

Then when you do a release update, you will be able to recognize the update.

I have to say though, the Intrepid Ibex release candidate, is working fine for me at the moment.

> **Sef said:**
> Before upgrading or clean installing, **back up** your **data**.  There are no guarantees that all will go well.

 Sef makes a good point- do back up your data-especially your customized configuration data.

---

### Post by poldie on 2008-10-29
> **meindian523 said:**
> Actually,it's recommended to do a clean install rather than do a distribution upgrade.If you have a separate /home partition,your personal settings shall be saved,but any editing of config files(may / may not be required in the new version,after all the kernel is new and might support your Wifi etc out of the box),if required,will have to be redone.This is true whether you clean install or allow the updater to do it's job.

Sounds like a good idea.  Not sure I remember having /home stored elsewhere was an installation option in Ubuntu 8.4 though.  I've had a bit of a google and found this guide:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Does this look like it's something which should work with 8.10?  I'd imagine this sort of thing is largely Distro independant, but what would I know? Is there another, better page with similar instructions I should be using?

Also, while I'm posting here,  I had a little look at the 64 bit version of 8.4.1, but didn't get anywhere because of problems with the browser (specifically support for flash and java, both of which I need working properly).  Is it likely that I'll run into problems with 8.10 64 bit?

---

### Post by poldie on 2008-10-29
> **mthei said:**
> 
a) the servers will probably be insanely busy (depending on your mirror, of course) 

Isn't that what torrents are for?

---

### Post by fendres on 2008-10-29
I have upgraded from 8.04.1 to 8.10 and it worked smoothly. However I do not know whether some bugs (it was beta then) could have been avoided by a clean install.

---

### Post by peakshysteria on 2008-10-29
> **tuxxy said:**
> I had hardly any issue with updating to Ibex, to update press ALT + F2 and enter

```
update-manager -d
```

Then you should see the option for dist upgrade :)

And what happened to your ATI setup? I'm very curious since everything is working hunky dory in my end already. But I would really like to upgrade and would like to know if an upgrade will break my ATI driver? Currently I'm running version 8.9 (latest is 8.10) on Ubuntu Hardy Heron 8.0.4.1 i686.

---

### Post by kline on 2008-10-29
The time before last I was content to hang with 6.06 LTS until I saw--to my happy surprise--that 8.04 was another LTS release.  So I d/loaded and everything, including my new widescreen, low-energy LCD display actually worked!!  When I asked about doing interim upgrades this time, somebody said that 8.10 was ready.  It wasn't and I've been stuck for weeks with a partly crippled version.  No audio, no widescreen (I'm guessing that this means that the SiS driver hasn't been merged into the latest).

Anyhow, in a day or two, hopefully, the new release will be done.  Will somebody post something here to let me know when it's safe to do the System->Admin->Upgrade ?

---

### Post by Pete317 on 2008-10-29
Well, I've been looking forward to tomorrow to upgrade to 8.10 and, hopefully, see an end to the multitude of problems I've had with Hardy.

However, I've just taken a look at the issues with Intrepid, and I'm now somewhat disillusioned.

Firstly, it seems that I won't be able to use 3d acceleration with my GeForce440 go, so I can forget about GoogleEarth and the like.

Secondly, there's no realtime kernel, so I can also forget about some of my audio recording stuff.

So it looks like I'm stuck with Hardy for the time-being, unless someone has a workaround for these important (to me) issues.

Sorry to sound so negative, just a bit disappointed I suppose.

---

### Post by mthei on 2008-10-29
> **poldie said:**
> Isn't that what torrents are for?

Right you are, but I meant in terms of doing an upgrade, rather than grabbing the new ISO.

---

### Post by poldie on 2008-10-29
> **mthei said:**
> Right you are, but I meant in terms of doing an upgrade, rather than grabbing the new ISO.

Sure.  Is there a reason, though, why torrents can't be the/a way of deploying both ISOs and upgrades.  I'm sure a lot of people/organisations would gladly provide a little bandwidth/diskspace for this sort of thing.  Perhaps, though, if it's only a problem twice a year and would cause a lot of trouble then there's a reason why it's not done.  But even Microsoft is looking into using torrents to distribute some content.

---

### Post by meindian523 on 2008-10-30
> **poldie said:**
> Sounds like a good idea.  Not sure I remember having /home stored elsewhere was an installation option in Ubuntu 8.4 though.  I've had a bit of a google and found this guide:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

Does this look like it's something which should work with 8.10?  I'd imagine this sort of thing is largely Distro independant, but what would I know? Is there another, better page with similar instructions I should be using?

Also, while I'm posting here,  I had a little look at the 64 bit version of 8.4.1, but didn't get anywhere because of problems with the browser (specifically support for flash and java, both of which I need working properly).  Is it likely that I'll run into problems with 8.10 64 bit?
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
This is preferable.Well known and tried and tested.Plus the author is aysiu here on Ubuntuforums,so can ask him if you have any doubts or problems.

---

### Post by Sef on 2008-10-30
> Also, while I'm posting here, I had a little look at the 64 bit version of 8.4.1, but didn't get anywhere because of problems with the browser (specifically support for flash and java, both of which I need working properly). Is it likely that I'll run into problems with 8.10 64 bit?

For Flash on Hardy, read [this tutorial]("http://ubuntuforums.org/showthread.php?t=772490").

For installing 32-bit Java on 64-bit Hardy, read [this tutorial]("http://ubuntuforums.org/showthread.php?t=202537&highlight=java").

OpenJDK is available Hardy.  It is open source Java.  For more information, read [this sticky]("http://ubuntuforums.org/showthread.php?t=774956").

---

### Post by Gausian on 2008-10-30
Ive had good success upgrading previous versions of Ubuntu, so theres nothing indicating it wont work this time.

---

### Post by fikelfikel on 2008-10-30
> **Gausian said:**
> Ive had good success upgrading previous versions of Ubuntu, so theres nothing indicating it wont work this time.

The upgrade didn't work for me. I think the servers are busy...

---

### Post by zika on 2008-10-30
>>You may not get all the new features (correct me if I'm wrong), but you'll still get all the newer versions of your installed packages

would You care to elaborate on this. what kind of features are {lost, missed, skipped} in upgrade vs. clean install?

---

### Post by 080818jk on 2008-10-30
[         &#19968;&#12289;&#31649;&#36947;&#30095;&#36890;&#19987;&#19994;&#26381;&#21153;:                        &#12288;&#12288; 1&#12289;&#39532;&#26742;&#30095;&#36890;&#65306;[&#30095;&#36890;&#31649;&#36947;](http://www.bjgdstgs.cn/stgd.htm)&#19987;&#19994;&#30095;&#36890;&#21508;&#31181;&#22411;&#21495;&#39532;&#26742;&#65288;&#25273;&#24067;&#12289;&#28165;&#27905;&#29699;&#12289;&#22609;&#26009;&#65289;&#31561;&#21508;&#31181;&#36719;&#30828;&#29289;&#36136;&#25152;&#36896;&#25104;&#30340;&#22581;&#22622;                        &#12288;&#12288;                                 2&#12289;&#22320;&#28431;&#30095;&#36890;&#65306;[&#31649;&#36947;&#30095;&#36890;](http://www.bjgdstgs.cn/gdst.htm)&#19987;&#19994;&#30095;&#36890;&#21508;&#31181;&#22411;&#25296;&#24367;&#30340;&#22320;&#28431;&#65292;&#21416;&#25151;&#30340;&#22320;&#28431;&#12289;&#21355;&#29983;&#38388;&#22320;&#27004;&#30340;&#22581;&#22622;&#65288;&#22240;&#20026;&#35013;&#20462;&#25481;&#36827;&#27700;&#27877;&#12289;&#27801;&#23376;&#25110;&#22836;&#21457;&#65289;&#31561;&#31181;&#21407;&#22240;&#25152;&#36896;&#25104;&#30340;&#22581;&#22622;&#12290;                                                     &#12288;&#12288;                                 3&#12289;&#22699;&#22353;&#30095;&#36890;&#65306;[&#31649;&#36947;&#30095;&#36890;](http://www.bjgdstgs.cn/gdst.htm)&#19987;&#19994;&#30095;&#36890;&#21508;&#31181;v&#22411;&#12289;S&#22411;&#25296;&#24367;&#30340;&#22320;&#28431;&#65292;&#22240;&#20026;&#22699;&#22353;&#24180;&#25104;&#20037;&#20102;&#65292;[&#21271;&#20140;&#31649;&#36947;&#30095;&#36890;](http://www.bjgdstgs.cn/bjgdst.htm)&#31649;&#36947;&#24367;&#22836;&#20135;&#29983;&#20102;&#19968;&#23618;&#21402;&#21402;&#30340;&#23615;&#30897;&#65292;&#30001;100&#21400;&#31859;&#24930;&#24930;&#30340;&#21464;&#25104;&#20102;50&#21400;&#31859;&#29978;&#33267;10&#21400;&#31859;&#29978;&#33267;&#36824;&#20250;&#22581;&#27515;&#65292;&#25152;&#20197;&#36896;&#25104;&#22699;&#22353;&#19979;&#27700;&#24930;&#12289;&#26131;&#22581;&#65292;&#26412;&#37096;&#26681;&#25454;&#22810;&#24180;&#25152;&#31215;&#32047;&#32463;&#39564;&#65292;[&#21271;&#20140;&#31649;&#36947;&#30095;&#36890;](http://www.bjgdstgs.cn/bjgdst.htm)&#37319;&#29992;&#26368;&#20339;&#25216;&#26415;&#21644;&#26041;&#26696;&#12289;&#24443;&#24213;&#30095;&#36890;&#21508;&#31181;&#24773;&#20917;&#25152;&#36896;&#25104;&#30340;&#22581;&#22622;

---

### Post by Dyffo on 2008-10-30
> **tuxxy said:**
> I had hardly any issue with updating to Ibex, to update press ALT + F2 and enter

```
update-manager -d
```

Then you should see the option for dist upgrade :)
When I try to upgrade I get this Error message:

A problem occurred during the update, this is usually some sort of network problem. please try again.

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas on how to resolve this. I have tried upgrading from the Terminal, synaptic etc - all come back with this error message.

---

### Post by meindian523 on 2008-10-30
Dyffo:
Please create a separate thread.

---

### Post by Jammy4041 on 2008-10-30
Dyffo- you need to go to software sources, and uncheck your cd.

---

### Post by Dyffo on 2008-10-30
Done and it worked - thanks

---

### Post by jtgurkin on 2008-10-30
I upgraded my server today and now the text screen font is HUGE.  I can't see most of the text only the "top left corner".  I can log in to ssh and everything is fine.  Can somebody give me a hint to fix this?


Thanks!

---

### Post by tripwire45 on 2009-01-28
Sorry to drag this one up out of the grave, but I followed the instructions to make the upgrade option from 8.04 to 8.10 available and used them on my Ubuntu VM last night. Worked like a charm and took less than 2 hours max. Only a couple of very small issues.

Whenever I launch an app like firefox, while the app is starting, the cursor seems to "jerk" on the screen. This might be a VMware issue rather than an upgrade issue, but I thought I'd mention it.

Also, the applet on the top panel that's used to edit the network connection has a white "X" over a red square, apparently indicating that networking is disabled. However, networking is fine. I've got access to my LAN and the Internet, but I can't figure out how to change the look of the applet, nor can I find an option for removing it from the panel.

Other than that, things seem to be ok, thus far.

---

