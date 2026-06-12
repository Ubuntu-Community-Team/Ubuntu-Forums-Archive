---
title: "wubi does not run"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by Bazmundi on 2012-05-30
To add insult to the 12.x upgrade breaking my 11.x installation, wubi will not run on my Acer laptop. It just spins its mouse pointer for a few seconds and never opens.

---

### Post by bcbc on 2012-05-30
> **Bazmundi said:**
> To add insult to the 12.x upgrade breaking my 11.x installation, wubi will not run on my Acer laptop. It just spins its mouse pointer for a few seconds and never opens.

This has been happening when wubi finds ISOs in the root of partitions that it can't. Check the log file in the %TEMP% directory. It should be clear which ISOs are at fault.
If that's not the problem, post the log file.

---

### Post by Bazmundi on 2012-05-31
> **bcbc said:**
> This has been happening when wubi finds ISOs in the root of partitions that it can't. Check the log file in the %TEMP% directory. It should be clear which ISOs are at fault.
If that's not the problem, post the log file.

If you mean my ...\AppData\Local\Temp directory the question would be which log?


Volume in drive C is Acer
 Volume Serial Number is DE8F-6BAE

 Directory of C:\Users\Asterion\AppData\Local\Temp

30/05/2012  09:41 AM               413 adb.log
31/05/2012  06:43 PM           487,149 AdobeARM.log
15/04/2012  06:07 PM               638 AdobeARM_NotLocked.log
31/05/2012  06:43 PM                 0 aipflib.log
10/06/2011  04:53 PM    <DIR>          BingBarInstallerLogs
04/12/2011  09:07 AM    <DIR>          BloggieStillUnwarp1051437365269296814temp
04/12/2011  09:08 AM    <DIR>          BloggieStillUnwarp1988811823049684143temp
04/12/2011  09:05 AM    <DIR>          BloggieStillUnwarp2483105754306918414temp
04/12/2011  09:08 AM    <DIR>          BloggieStillUnwarp3907242447562451267temp
04/12/2011  09:07 AM    <DIR>          BloggieStillUnwarp6366343366876183719temp
04/12/2011  09:10 AM    <DIR>          BloggieStillUnwarp6581603196390685394temp
04/12/2011  09:10 AM    <DIR>          BloggieStillUnwarp6765054040407682872temp
04/12/2011  09:05 AM    <DIR>          BloggieStillUnwarp954114029255666458temp
04/12/2011  12:16 PM    <DIR>          BloggieVideoUnwarp1376092267704136573temp
04/12/2011  12:34 PM    <DIR>          BloggieVideoUnwarp149314261557997897temp
04/12/2011  12:34 PM    <DIR>          BloggieVideoUnwarp3110664354874699509temp
04/12/2011  10:35 AM    <DIR>          BloggieVideoUnwarp391182210746950088temp
04/12/2011  10:35 AM    <DIR>          BloggieVideoUnwarp396975014453594585temp
04/12/2011  12:16 PM    <DIR>          BloggieVideoUnwarp4121540925864657619temp
04/12/2011  10:20 AM    <DIR>          BloggieVideoUnwarp4380543875915613804temp
04/12/2011  10:29 AM    <DIR>          BloggieVideoUnwarp4410101699441000304temp
04/12/2011  10:35 AM    <DIR>          BloggieVideoUnwarp4499182751132233216temp
04/12/2011  10:35 AM    <DIR>          BloggieVideoUnwarp4924165898019068623temp
04/12/2011  12:34 PM    <DIR>          BloggieVideoUnwarp636638183917110826temp
04/12/2011  10:35 AM    <DIR>          BloggieVideoUnwarp741735253145920904temp
04/12/2011  10:20 AM    <DIR>          BloggieVideoUnwarp7587270839495703994temp
04/12/2011  12:34 PM    <DIR>          BloggieVideoUnwarp7712636617430617833temp
04/12/2011  10:35 AM    <DIR>          BloggieVideoUnwarp7771358430646271968temp
04/12/2011  12:34 PM    <DIR>          BloggieVideoUnwarp8545071101714436306temp
04/12/2011  10:29 AM    <DIR>          BloggieVideoUnwarp8617184492223496610temp
04/12/2011  12:15 PM    <DIR>          BloggieVideoUnwarp8717934233311906446temp
04/12/2011  12:34 PM    <DIR>          BloggieVideoUnwarp8788360912638312745temp
04/12/2011  12:15 PM    <DIR>          BloggieVideoUnwarp9201108027197270947temp
25/05/2012  12:05 PM             3,629 chrome_installer.log
22/05/2012  12:52 PM    <DIR>          CitrixLogs
10/06/2011  04:48 PM                 0 FXSAPIDebugLogFile.txt
31/05/2012  06:48 PM           120,254 jusched.log
24/05/2012  05:27 PM            18,348 KiesInstall.Log
31/05/2012  06:43 PM                 0 LManager.log
31/05/2012  06:43 PM                 0 LMworker.log
31/05/2012  07:06 PM                 0 log.txt
31/05/2012  07:06 PM            26,756 lxdoscan.log
13/05/2012  11:09 AM           879,080 MSI3146a.LOG
15/04/2012  08:28 PM            38,384 MSI4ef29.LOG
15/04/2012  08:30 PM         1,616,596 MSI551c2.LOG
08/10/2011  11:59 AM    <DIR>          outlook logging
18/05/2012  02:30 PM             2,705 QTInstallCode.log
18/05/2012  02:30 PM             3,411 qtplugin.log
28/03/2012  05:13 PM             2,378 SketchUpUndo0.log
10/04/2012  06:46 PM             5,414 StructuredQuery.log
31/05/2012  06:43 PM             8,774 tbpwbcm.log
28/04/2012  01:09 PM             2,700 tbp_wbb_driverinstall.log
25/04/2012  12:19 PM             1,102 Unnamed1.log.xml
31/05/2012  05:04 PM           161,913 vminst.log
31/05/2012  02:51 PM           322,744 vmsetup.20120531144800.log
31/05/2012  02:51 PM            56,420 vmsetup.20120531144824.log
31/05/2012  02:48 PM           153,128 vmsetup.20120531144824.{003BFBBD-6C67-419E-A24D-0DCAFC3A5249}.uninstall.log
31/05/2012  02:51 PM         3,002,662 vmsetup.20120531144824.{A53A11EA-0095-493F-86FA-A15E8A86A405}.uninstall.log
31/05/2012  02:48 PM           153,064 vmsetup.20120531144824.{D102611A-6466-4101-A51D-51069303AC65}.uninstall.log
31/05/2012  05:05 PM           325,272 vmsetup.20120531165713.log
31/05/2012  05:04 PM         3,014,766 vmsetup.20120531165713.vmware player.msi.install.log
31/05/2012  04:58 PM           130,494 vmsetup.20120531165713.vmwarevmcisockets64.msi.install.log
31/05/2012  05:04 PM            25,138 vmsetup.20120531170438.log
31/05/2012  05:04 PM           169,146 vmsetup.20120531170438.tools-freebsd.msi.install.log
31/05/2012  05:05 PM            31,994 vmsetup.20120531170447.log
31/05/2012  05:05 PM           168,970 vmsetup.20120531170447.tools-linux.msi.install.log
31/05/2012  02:51 PM             1,880 vmUpdateLauncher-8520.log
23/04/2012  03:14 PM             2,462 wmplog00.sqm
25/04/2012  08:37 AM             1,646 wmplog01.sqm
25/04/2012  09:02 AM             1,502 wmplog02.sqm
13/05/2012  02:04 PM             1,662 wmplog03.sqm
13/05/2012  06:10 PM             1,526 wmplog04.sqm
24/05/2012  10:38 AM             1,766 wmplog05.sqm
24/05/2012  10:39 AM             1,502 wmplog06.sqm
24/05/2012  10:39 AM             1,502 wmplog07.sqm
24/05/2012  10:40 AM             1,502 wmplog08.sqm
24/05/2012  10:40 AM             1,502 wmplog09.sqm
24/05/2012  10:40 AM             1,502 wmplog10.sqm
              47 File(s)     10,953,396 bytes
              31 Dir(s)  474,798,403,584 bytes free

None of them look obviously wubi generated.

---

### Post by Lyfang on 2012-05-31
> **Bazmundi said:**
> To add insult to the 12.x upgrade breaking my 11.x installation, wubi will not run on my Acer laptop. It just spins its mouse pointer for a few seconds and never opens.

Sorry to hear about that. You can boot using a Ubuntu Live CD or Live USB & mount the root.disk to recover your personal files. I wrote about this in Swedish @ Linuxportalen [http://www.linuxportalen.se/blogs/lyfang/2011/05/15/hur-kommer-man-t-wubi-ubuntumint4win-linux-mint-filerna-om-inte-att-wubimint](http://www.linuxportalen.se/blogs/lyfang/2011/05/15/hur-kommer-man-t-wubi-ubuntumint4win-linux-mint-filerna-om-inte-att-wubimint)

Then reinstall Ubuntu with Wubi: [http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

---

### Post by Bazmundi on 2012-05-31
> **Lyfang said:**
> Sorry to hear about that. You can boot using a Ubuntu Live CD or Live USB & mount the root.disk to recover your personal files. I wrote about this in Swedish @ Linuxportalen [http://www.linuxportalen.se/blogs/lyfang/2011/05/15/hur-kommer-man-t-wubi-ubuntumint4win-linux-mint-filerna-om-inte-att-wubimint](http://www.linuxportalen.se/blogs/lyfang/2011/05/15/hur-kommer-man-t-wubi-ubuntumint4win-linux-mint-filerna-om-inte-att-wubimint)

Then reinstall Ubuntu with Wubi: [http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

They may or may not be possible.  I went to the Control Panel to uninstall ubuntu.  When I ran the uninstall it appeared either not to work or at least not lift remnants out of the system as it remained in the the Control Panel list.

I have since pulled out dbdedit to remove ubuntu from the boot and also regedit to lift it out of registry.

This may have been a little extreme but the unofficial line appears to be that the wubi version over windows is just an unsupported toy to be used to trial ubuntu.  I assume no one tested the 11.10 wubi install against a 12.whatzit update - which left me with a blue background and a mouse, and nothing else.

I will have a look at your page and see what I can do to clean ubuntu off my machine.  Thanks.

---

### Post by bcbc on 2012-05-31
It's the %TEMP% directory (that's an environment variable) and the logfile is wubi-12.04-rev266.log.

I guess that's just a comment for anyone else, if you don't need it anymore.

Ubuntu upgrades do fail - it doesn't have anything to do with Wubi (that was true in the past certainly). Wubi upgrades probably tend to fail more because they don't have lots of free space typically (you need about 3GB minimum and there is a bug in the upgrade manager that will let you upgrade with <2GB.). But that's not the only reason they fail.

Wubi is designed to try out Ubuntu. Maybe you could call it a toy. Sure, why not. It's definitely not a recommended way to run a 'production OS' if that's what you mean.

---

### Post by Bazmundi on 2012-05-31
> **bcbc said:**
> It's the %TEMP% directory (that's an environment variable) and the logfile is wubi-12.04-rev266.log.

I guess that's just a comment for anyone else, if you don't need it anymore.

Ubuntu upgrades do fail - it doesn't have anything to do with Wubi (that was true in the past certainly). Wubi upgrades probably tend to fail more because they don't have lots of free space typically (you need about 3GB minimum and there is a bug in the upgrade manager that will let you upgrade with <2GB.). But that's not the only reason they fail.

Wubi is designed to try out Ubuntu. Maybe you could call it a toy. Sure, why not. It's definitely not a recommended way to run a 'production OS' if that's what you mean.

As you say, %TEMP% resolves to ...\AppData\Local\Temp so it appears the uninstall for wubi doesn't work properly.  It leaves the ubuntu in the dual boot, fragments in the registry, wubi files on disk.  All in all bad form.  If it is supposed to only be a teaser then a well behaved demo will unsinstall.

Now given that all this information is coming post calamity I have to say tich tich.  Someone has to be grown up and put something on [http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows) to say it is not recommended as a production tool, does not update without breaking and will not unistall ](*,)

At least someone can bother to put up a post on how to manually remove the wubi installation from your machine - might be novel to have the author of wubi do it, could catch on (it would also be the honorable thing to do).

---

### Post by bcbc on 2012-05-31
> **Bazmundi said:**
> As you say, %TEMP% resolves to ...\AppData\Local\Temp so it appears the uninstall for wubi doesn't work properly.  It leaves the ubuntu in the dual boot, fragments in the registry, wubi files on disk.  All in all bad form.  If it is supposed to only be a teaser then a well behaved demo will unsinstall.

Now given that all this information is coming post calamity I have to say tich tich.  Someone has to be grown up and put something on [http://www.ubuntu.com/download/help/install-ubuntu-with-windows](http://www.ubuntu.com/download/help/install-ubuntu-with-windows) to say it is not recommended as a production tool, does not update without breaking and will not unistall ](*,)

At least someone can bother to put up a post on how to manually remove the wubi installation from your machine - might be novel to have the author of wubi do it, could catch on (it would also be the honorable thing to do).

It usually uninstalls normally. There is obviously a reason that it failed. The first step would be to post the log file so someone can review it. Post the 11.10 logfile if that's the release you're trying to uninstall. I can give some examples of why it might fail e.g. you did a windows restore, the ubuntu virtual disk is corrupted, you removed part of it manually... etc.

There are reasons why upgrades fail as well. It's possible that it's wubi related, but there really is no reason a wubi install should fail to upgrade (that's different from a normal install). Again, it's something that could be investigated but it requires some work on your part (and it sounds like you've deleted it already).

And here is what you're looking for: [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

