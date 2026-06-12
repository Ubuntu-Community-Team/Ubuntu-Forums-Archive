---
title: "Laptop Load Cycle Bug Finally Fixed!"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sand Lee on 2008-10-08
_[[SIZE="4"]EpicBugReport[/SIZE]]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695")_
_[[SIZE="3"]**Changelog**[/SIZE]]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695#546")_
_**Bart Samwel's** Description:_
> The fix that has now been applied is the Debian fix, which purposely
leaves the power management (and therefore the cycling) enabled when the
laptop is working on battery. This is for safety reasons: it is assumed
that the laptop is working on battery when it is being carried around,
and it is much safer to park the heads in such situations. Also, we did
not want to increase the power usage while in battery mode! This does
mean that the drive lifetime still becomes shorter, but since
battery-mode usage is limited by battery life span, required recharge
times, and general usage patterns, this is already a much safer
situation. (This is, however, not configurable. If you want that,
install laptop-mode-tools and let that handle it. The acpi-support fix
detects if laptop-mode-tools handles it, and leaves it to
laptop-mode-tools in that case.)

Cheers,
Bart
The fix should hit your laptops tomorrow.
:guitar: [[SIZE="3"][COLOR="DarkOliveGreen"]**Digg This Story**[/COLOR][/SIZE]]("http://digg.com/linux_unix/Laptop_Hard_Drive_Bug_Fixed_in_Ubuntu")

---

### Post by olskar on 2008-10-08
Wow! Finally after two years! Celebration time! :guitar:

---

### Post by aidave on 2008-10-08
sweet

---

### Post by mc4100 on 2008-10-08
I can't wait to see the results: the bug report says symptoms are more than one click every 3 mins. And, often, I'm hearing one about every 3 **seconds**.

---

### Post by zombiepig on 2008-10-08
So - if I understand this correctly, it fixes it while on power, but the problem still exists if you're running on battery?

---

### Post by Sand Lee on 2008-10-08
> **zombiepig said:**
> So - if I understand this correctly, it fixes it while on power, but the problem still exists if you're running on battery?

No, the parking is actually supposed to happen on battery. I believe the fix should have parking set to a moderate level though. It saves battery life, cools your hard disk, and protects our hard drive from bumps.

---

### Post by damis648 on 2008-10-08
Awesome!:popcorn:

---

### Post by frogotronic on 2008-10-09
Is this in Ubuntu yet?

- CH

---

### Post by MacUntu on 2008-10-09
What about resuming from standby? Teh APM value always got set back to 128 for me. I fixed the original problem with "hdparm -B 254 /dev/sda" in my rc.local which worked fine except for resuming...

---

### Post by Sand Lee on 2008-10-09
1000 views, and only 61 diggs...:confused:

---

### Post by zombiepig on 2008-10-09
> **MacUntu said:**
> What about resuming from standby? Teh APM value always got set back to 128 for me. I fixed the original problem with "hdparm -B 254 /dev/sda" in my rc.local which worked fine except for resuming...

I'm seeing the same now - the cycling is fixed until I suspend/resume. I've added a comment to the bug report linked to on the first page of this thread, can you confirm it's also happening for you?

---

### Post by njk123 on 2008-10-09
Should those who have ugly fix currently installed do anything special or just wait for the update?

---

### Post by MacUntu on 2008-10-10
> **zombiepig said:**
> I'm seeing the same now - the cycling is fixed until I suspend/resume. I've added a comment to the bug report linked to on the first page of this thread, can you confirm it's also happening for you?

Yes. :(

---

### Post by blackhole54 on 2008-10-10
> **olskar said:**
> Wow! Finally after two years! Celebration time! 


I suppose if you overclock your universe by about a factor of two, maybe it is two years.  For the rest of us, it has only been about 1 year.  (It just seems longer.) ;)

---

### Post by olskar on 2008-10-10
> **blackhole54 said:**
> I suppose if you overclock your universe by about a factor of two, maybe it is two years.  For the rest of us, it has only been about 1 year.  (It just seems longer.) ;)

Now you are confusing me :(

The bug was reported 2006-09-09 ~ two years ago? Or how you underclocked your universe and are stuck in 2007? ;)

---

### Post by blackhole54 on 2008-10-11
> **olskar said:**
> The bug was reported 2006-09-09 ~ two years ago? Or how you underclocked your universe and are stuck in 2007? ;)

Oops!  :redface:

I don't think it was as much a problem with underclocking as an overly restrictive firewall! (Not enough packets getting through.)  I didn't check back (this time) to the original bug report.  I was going on memory, and the problem came on my radar screen (after the Load_Cycle_Count on my relatively new laptop [was over 600,000](http://ubuntuforums.org/showthread.php?t=594796)) about a year ago with the appearance of [articles like this](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear).

Anyway, its good there is now a "permanent" fix.

Now if you'll excuse me while I try to dislodge my foot from my mouth ...

---

### Post by frodon on 2008-10-14
Sounds a workaround for me rather than fix. Heads park crazily because the kernel stimulate too often the disk and if this has not been changed therefore you will still have the crazy behaviour on battery which is better but not i would call a "fix".

A fix would be to mofify the kernel to handle syslog, ext3 journal, core processes in a way that they do what they have to do all together at the same time reducing the frequency of the disk stimulation and making the thread parking really efficient.

I think i will still keep the "ugly" fix which is in fact as ugly as this one for me :p

I honestly hope they dealt with the laptop-mode hang issues if they advice laptop-mode-tools, i always thought laptop-mode was not developed anymore. Time will tell us.

Sorry for not being enthusiastic like you are but i feel nothing has really moved yet to enhance things at the kernel side which is inescapable for a real solution. I can't be satisfied by just a workaround added by default which however a great step forward for users not aware of this.

---

### Post by olskar on 2008-10-14
> **frodon said:**
> Sounds a workaround for me rather than fix. Heads park crazily because the kernel stimulate too often the disk and if this has not been changed therefore you will still have the crazy behaviour on battery which is better but not i would call a "fix".

A fix would be to mofify the kernel to handle syslog, ext3 journal, core processes in a way that they do what they have to do all together at the same time reducing the frequency of the disk stimulation and making the thread parking really efficient.

I think i will still keep the "ugly" fix which is in fact as ugly as this one for me :p

I honestly hope they dealt with the laptop-mode hang issues if they advice laptop-mode-tools, i always thought laptop-mode was not developed anymore. Time will tell us.

Sorry for not being enthusiastic like you are but i feel nothing has really moved yet to enhance things at the kernel side which is inescapable for a real solution. I can't be satisfied by just a workaround added by default which however a great step forward for users not aware of this.

The real "fix" would be if the harddrive-manufacturers fixed their harddrives I think :) Anyway I think a workaround is better then nothing for new people coming to Ubuntu and wondering why their harddrive is clicking a lot and finally dies.

---

### Post by frodon on 2008-10-14
Hardrive manufacturers can set safer default setting this is true but if when your heads parks your kernel ask data right after as it is the case now it almost nulify the head parking interest as your head unpark right after being parked.

Anyway it is as you said a great step forward for new users, i hope it will be simple to deactivate this acpi workaround in order use the pm-util one for advanced users.

---

### Post by Sealbhach on 2008-10-20
I was still getting nasty clicking sounds every 20 seconds so I installed the "ugly fix" again from Hardy. It seems to have stopped it.

So for me,I don't think Intrepid has fixed it.



.

---

### Post by midnightflash on 2008-10-20
> **Sealbhach said:**
> So for me,I don't think Intrepid has fixed it.Dito. For me neither.

---

### Post by linusr on 2008-10-26
Dito. Not fixed on my Dell Vostro 1500.

Load_Cycle keeps increasing....

---

### Post by blackhole54 on 2008-10-27
**(For those who are having problems with this fix but don't wish to wade through my analysis, please skip down about half way for some tests to run.)**

I was intrigued by all the reports that this fix doesn't work.  So I decided to take a look at what is being done.  I don't have an up-to-date Ubuntu system, so this was just downloading what I think is the right package and looking at the relevant scripts in it.  It appears to me that it is basically the "ugly fix" with some sanity checks added.  I'd appreciate if people who have *Intrepid* and are familiar with shell scripting double check me on this.

I downloaded acpi-support_0.114_i386.deb.  (Did I get the right package?)

I then examined the following scripts (note the braces in the path) in it:
/etc/acpi/{resume.d,start.d,ac.d,battery.d}/90-hdparm.sh

These scripts are all identical.  (Wouldn't a single script with symlinks be better?)

If $CONTROL_HD_POWERMGMT in laptop-mode.conf is zero, and for drives that report "AdvancedPM=yes", these scripts set the disk APM value to 128 or 254 if the computer is on battery or AC, respectively. [color=red](Corrected:  originally I wrote this backwards.)[/color]

I see two possible points of failure with this scheme.

[LIST]
[*]laptop-mode.conf is checked w/o actually checking to make sure that laptop-mode itself is running.  My guess is this will work properly on a default install, but if a user has configured laptop-mode and either never enabled it or turned it back off, this test may erroneously refuse to adjust disk APM.
[*]As noted in **90-hdparm.sh**, some drives don't support HDIO_GET_IDENTITY (hdparm -i).  I have such a drive.  My reading of the script is that this is another case where it would refuse to adjust disk APM even though the disk may support doing so.
[/LIST]

Otherwise it looks like the "ugly fix" to me.

That is my analysis.  I would appreciate people comfortable with shell scripting to double check it.  I have not considered whether this script should be in additional locations.

For those that are reporting that this isn't working, I have a couple suggestions/requests.

Check and see what your disk's APM state is both when on battery and when on AC.  For example, right now mine reports:

```

Advance power management level:  254 (0xfe)

```

Different disks may phrase this slightly differently, but the following command will probably get the desired info:

```

sudo hdparm -I /dev/sda | grep -i power

```

Also check to see if the following command produces an error:

```

sudo hdparm -i /dev/sda

```

Take care to note that the options for those two  **hdparm** commands use different cases (first one is upper case, second one is lower case).

---

### Post by linusr on 2008-10-27
both on AC & batery power Vostro 150,

Advanced power management level: 254

but i did edit hdparm.conf, to set '254' value for /dev/sda

before editing hdparm.cong load cycle on ubuntu 8.10 fresh install kept increasing every second

---

### Post by Jay_Bee on 2008-10-27
I am too still affected by this bug... load cycle is still increasing:(
Advanced power management level: 128

---

### Post by blackhole54 on 2008-10-27
@ linusr & Jay_Bee

did you try

```

sudo hdparm -i /dev/sda

```

to see if it produced an error?

@ Jay_Bee

is APM at 128 on both battery and AC?

BTW, it sounds like *linusr* might have a work-around for you to stop the increase.  Just be aware that (I think) that work-around leaves the APM at 254 even while on battery, which means the disk might be a bit more vulnerable to being bumped, etc than it would at 128.

---

### Post by Jay_Bee on 2008-10-28
Thanks for your help.
```

sudo hdparm -i /dev/sda

```
Didn't produce an error, it showed various info about my hdd.
```
/dev/sda:

 Model=Hitachi HTS541616J9SA00                 , FwRev=SB4OC7BP, SerialNo=      SB2404GJHKJ5YE
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=7516kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312581808
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 1:  ATA/ATAPI-2,3,4,5,6,7

```
APM is 128 on both battery and AC...
I'm thinking about installing the ugly-fix again because load cycle stops increasing when I set APM to 254.

---

### Post by linusr on 2008-10-28
Thanks blackhole54,

no errors for sudo > hdparm -i /dev/sda,

output,
> 
/dev/sda:

 Model=ST9160821AS                             , FwRev=3.CDD   , SerialNo=            5MA4BP5H
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=?8?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312581808
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

I dont see any noise or overheating at APM 254. so far works good.

---

### Post by blackhole54 on 2008-10-29
@ linusr & Jay_Bee

Thanks for your replies.  While I noted above what seems to be couple of weaknesses in the scripts that are supposed to control this, I don't see any reason why the scripts shouldn't be working for you two.

@ Jay_Bee

Since you (TMK)  still have the default setup where it's not working, I wonder if you would mind trying to run the script manually (while on AC) and see if it switches your APM setting over to 254:

```

sudo /etc/acpi/ac.d/90-hdparm.sh
sudo hdparm -I /dev/sda | grep -i power

```

First make sure the file /etc/acpi/ac.d/90-hdparm.sh is actually there.  (Remember I don't have *Intrepid*; I am just working from a downloaded .deb package.)  If it still doesn't switch disk APM to 254 and if it doesn't spit out any errors, I wonder if you would do one more step of troubleshooting:

Make an extra copy of that file to your home directory or the /tmp directory

```

#  To home directory (note the "space dot" at the end:
cp /etc/acpi/ac.d/90-hdparm.sh .        

#  Or to the /tmp directory.  If you do this, this copy
#  of the file will vanish at the next bootup.
cp /etc/acpi/ac.d/90-hdparm.sh /tmp

```

Then use your favorite text editor (such as gedit, vi, etc.) on that file.
1)  First please verify the file looks like what I am posting below minus the line I've highlighted in red.
2)  If it looks the same, add the line I've highlighted and try running this modified file and post the output please.  To run it, use the command below that is appropriate to where you copied the file.

```

#  If in your home directory:
sudo ./90-hdparm.sh

#  If in the temp directory:
sudo /tmp/90-hdparm.sh

```

Here is what I believe the file looks like, with that one extra line added.  (That line will show what actually happens as the script executes and hopefully allow us to determine what is going wrong and maybe get this thing fixed.)

```

#! /bin/sh
#
# This script adjusts hard drive APM settings using hdparm. The hardware
# defaults (usually hdparm -B 128) cause excessive head load/unload cycles
# on many modern hard drives. We therefore set hdparm -B 254 while on AC
# power. On battery we set hdparm -B 128, because the head parking is
# very useful for shock protection.
#

. /usr/share/acpi-support/power-funcs

[color=red]set -x[/color]
DO_HDPARM=y
if [ -e /usr/sbin/laptop_mode ] ; then 
  LMT_CONTROL_HD_POWERMGMT=$(. /etc/laptop-mode/laptop-mode.conf && echo "$CONTROL_HD_POWERMGMT")
  if [ "$LMT_CONTROL_HD_POWERMGMT" != 0 ] ; then
    # Laptop mode controls hdparm -B settings, we don't.
    DO_HDPARM=n
  fi
fi

if [ $DO_HDPARM = y ] ; then
  # Get the power state into STATE
  getState;
  
  for dev in /dev/sd? /dev/hd? ; do
    if [ -b $dev ] ; then
      # Check for APM support; discard errors since not all drives
      # support HDIO_GET_IDENTITY (-i).    
      if hdparm -i $dev 2> /dev/null | grep -q 'AdvancedPM=yes' ; then
        if [ $STATE = "BATTERY" ] ; then
          hdparm -B 128 $dev
        else
          hdparm -B 254 $dev
        fi
      fi
    fi
  done
fi

```

Thanks for your patience with this.

EDIT:   Be aware that if you install the "ugly fix" w/o removing these new scripts you might have some intereaction between the two.

---

### Post by Jay_Bee on 2008-10-29
I just noticed after the restart that APM is 254 but after resuming from suspend it resets to 128. All this time I am on AC.
I apologize for the wrong information, but nevertheless the issue still exists.
So, after resuming from suspend, I tried your modification and this is the output of the modified file... 

```
$ ./90-hdparm.sh 
+ DO_HDPARM=y
+ [ -e /usr/sbin/laptop_mode ]
+ . /etc/laptop-mode/laptop-mode.conf
+ VERBOSE_OUTPUT=0
+ ENABLE_LAPTOP_MODE_ON_BATTERY=1
+ ENABLE_LAPTOP_MODE_ON_AC=0
+ ENABLE_LAPTOP_MODE_WHEN_LID_CLOSED=0
+ MINIMUM_BATTERY_CHARGE_PERCENT=3
+ DISABLE_LAPTOP_MODE_ON_CRITICAL_BATTERY_LEVEL=1
+ HD=/dev/[hs]d[abcdefgh]
+ PARTITIONS=auto /dev/mapper/*
+ ASSUME_SCSI_IS_SATA=1
+ LM_BATT_MAX_LOST_WORK_SECONDS=600
+ LM_AC_MAX_LOST_WORK_SECONDS=360
+ CONTROL_READAHEAD=1
+ LM_READAHEAD=3072
+ NOLM_READAHEAD=128
+ CONTROL_NOATIME=0
+ USE_RELATIME=1
+ CONTROL_HD_IDLE_TIMEOUT=1
+ LM_AC_HD_IDLE_TIMEOUT_SECONDS=60
+ LM_BATT_HD_IDLE_TIMEOUT_SECONDS=60
+ NOLM_HD_IDLE_TIMEOUT_SECONDS=7200
+ CONTROL_HD_POWERMGMT=1
+ BATT_HD_POWERMGMT=1
+ LM_AC_HD_POWERMGMT=254
+ NOLM_AC_HD_POWERMGMT=254
+ CONTROL_HD_WRITECACHE=0
+ NOLM_AC_HD_WRITECACHE=1
+ NOLM_BATT_HD_WRITECACHE=0
+ LM_HD_WRITECACHE=0
+ CONTROL_MOUNT_OPTIONS=1
+ LM_DIRTY_RATIO=60
+ NOLM_DIRTY_RATIO=40
+ LM_DIRTY_BACKGROUND_RATIO=1
+ NOLM_DIRTY_BACKGROUND_RATIO=10
+ DEF_UPDATE=5
+ DEF_XFS_AGE_BUFFER=15
+ DEF_XFS_SYNC_INTERVAL=30
+ DEF_XFS_BUFD_INTERVAL=1
+ DEF_MAX_AGE=30
+ XFS_HZ=100
+ LM_SECONDS_BEFORE_SYNC=2
+ echo 1
+ LMT_CONTROL_HD_POWERMGMT=1
+ [ 1 != 0 ]
+ DO_HDPARM=n
+ [ n = y ]

```

However after manually running the script the APM is still 128.
```
$ sudo hdparm -I /dev/sda | grep -i power
	Advanced power management level: 128
	   *	Power Management feature set
	   *	Advanced Power Management feature set
	    	Device-initiated interface power management

```

I will now try and see what's the output when I run the modified script after the restart (when it apparently works)
Thank you very much for your effort.

EDIT: The output after restarting is the same...
EDIT2: Hmmm... DO_HDPARM=n because CONTROL_HD_POWERMGMT=1 in laptop-mode.conf... Why set that as default?

EDIT 3 : 
Sorry for the furious edits...
I changed the CONTROL_HD_POWERMGMT to 0 and after resuming the value remained 128 but running your script did the trick
```
$ sudo ./90-hdparm.sh 
+ DO_HDPARM=y
+ [ -e /usr/sbin/laptop_mode ]
+ . /etc/laptop-mode/laptop-mode.conf
+ VERBOSE_OUTPUT=0
+ ENABLE_LAPTOP_MODE_ON_BATTERY=1
+ ENABLE_LAPTOP_MODE_ON_AC=0
+ ENABLE_LAPTOP_MODE_WHEN_LID_CLOSED=0
+ MINIMUM_BATTERY_CHARGE_PERCENT=3
+ DISABLE_LAPTOP_MODE_ON_CRITICAL_BATTERY_LEVEL=1
+ HD=/dev/[hs]d[abcdefgh]
+ PARTITIONS=auto /dev/mapper/*
+ ASSUME_SCSI_IS_SATA=1
+ LM_BATT_MAX_LOST_WORK_SECONDS=600
+ LM_AC_MAX_LOST_WORK_SECONDS=360
+ CONTROL_READAHEAD=1
+ LM_READAHEAD=3072
+ NOLM_READAHEAD=128
+ CONTROL_NOATIME=0
+ USE_RELATIME=1
+ CONTROL_HD_IDLE_TIMEOUT=1
+ LM_AC_HD_IDLE_TIMEOUT_SECONDS=60
+ LM_BATT_HD_IDLE_TIMEOUT_SECONDS=60
+ NOLM_HD_IDLE_TIMEOUT_SECONDS=7200
+ CONTROL_HD_POWERMGMT=0
+ BATT_HD_POWERMGMT=1
+ LM_AC_HD_POWERMGMT=254
+ NOLM_AC_HD_POWERMGMT=254
+ CONTROL_HD_WRITECACHE=0
+ NOLM_AC_HD_WRITECACHE=1
+ NOLM_BATT_HD_WRITECACHE=0
+ LM_HD_WRITECACHE=0
+ CONTROL_MOUNT_OPTIONS=1
+ LM_DIRTY_RATIO=60
+ NOLM_DIRTY_RATIO=40
+ LM_DIRTY_BACKGROUND_RATIO=1
+ NOLM_DIRTY_BACKGROUND_RATIO=10
+ DEF_UPDATE=5
+ DEF_XFS_AGE_BUFFER=15
+ DEF_XFS_SYNC_INTERVAL=30
+ DEF_XFS_BUFD_INTERVAL=1
+ DEF_MAX_AGE=30
+ XFS_HZ=100
+ LM_SECONDS_BEFORE_SYNC=2
+ echo 0
+ LMT_CONTROL_HD_POWERMGMT=0
+ [ 0 != 0 ]
+ [ y = y ]
+ getState
+ /usr/bin/on_ac_power
+ [ 0 -eq 0 ]
+ STATE=AC
+ [ -b /dev/sda ]
+ hdparm -i /dev/sda
+ grep -q AdvancedPM=yes
+ [ AC = BATTERY ]
+ hdparm -B 254 /dev/sda

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
+ [ -b /dev/hd? ]

```

Now... how to make the script actually run on resume?

---

### Post by blackhole54 on 2008-10-30
Thanks for hanging in there Jay_Bee, and don't worry about the number of edits.  It's obvious that you are starting to piece this together in your own mind, and that is good.  (I have no idea whether you've had any experience with shell scripts before and I've asked you to do things that would scare some people.)  If we can get this solved, and if nobody else has already file a bug report, I hope to file a bug report referencing this thread.

Just so you know, that statement I had you add should not change what the script actually does.  It just causes the script to show each line that it executes (sort of) so we can tell what is happening.  (And I didn't think about all of the lines that would be spit out as a result of it "sourcing" laptop-mode.conf.  :-/ ) 

> **Jay_Bee said:**
> 
EDIT2: Hmmm... DO_HDPARM=n because CONTROL_HD_POWERMGMT=1 in laptop-mode.conf... Why set that as default?

I am a bit surprised, because in *Edgy* (the reference I have) the default was 0.  But as I pointed out in post #23 I think the script needs to be modified to not even check that unless lapt-mode is running.  But we shouldn't need to worry about that to get you up and running.

> 
I changed the CONTROL_HD_POWERMGMT to 0 and after resuming the value remained 128 but running your script did the trick. ...

Now... how to make the script actually run on resume?

Just to double check that we understand each other, let me recap ...

After changing CONTROL_HD_POWERMGMT to 0 (in laptop-mode.conf), manually running the modified script gives the expected result.  That means the unmodified script should work also.  You can easily verify this:

```

sudo /etc/acpi/ac.d/90-hdparm.sh
sudo hdparm -I /dev/sda | grep -i power

```

(You should start whith the disk's APM _not_ set to 254 just to make sure the script actually did something!)

My belief is that copies of that script (90-hdparm.sh) exist in the following directories:

```

/etc/acpi/resume.d
/etc/acpi/start.d
/etc/acpi/ac.d
/etc/acpi/battery.d

```

Could you double check that for me?  If you want to make sure the files are in fact identical, you can use commands like:

```

cmp /etc/acpi/resume.d/90-hdparm.sh /etc/acpi/start.d/90-hdparm.sh

```

which will compare those two files.  If the command produces no outptut, the files are the same.  (See note below about "tab completion" if you don't already know about it.)

So if the unmodified script works (when run manually) and if it is in all of the locations I just mentioned, then I would think it should handle things correctly at start, when resuming from suspend or hibernate, and when switching to/from battery.  If it does not, I may not be able to help you troubleshoot further.  Please post back when you know for sure whether that is where we are.

If there is anybody else following this thread who has an idea about this, please post! Otherwise I might just need to file the bug report w/o the complete solution and see what the developers come up with.



TAB COMPLETION:

You can save yourself a great deal of effort with commands that involve long path/filenames (and commands to!) like the **cmp** command above by using "tab completion."  In that example, it you start typing "/etc/ac" and then hit the tab key, it will (at least partially) complete the rest if there is no ambiguity.  In this case it will get you to "/etc/acpi/".  You can type some more, hit tab again, etc., until finished with the parameter.  If there is an ambiguity when you hit tab, it will beep.  Just type another character or two and hit tab again.  You can do this as many times in a command line as wish.  And save yourself a lot of typing!

ANOTHER TRICK:

If you are going to run a series of commands that are almost the same, such as the three commands to compare those four files above, you can hit the "up arrow" on your keyboard to recall the previous command and then use left/right arrows, backspace and delete keys to make minor alterations. This is another great way to avoid typing.

---

### Post by Jay_Bee on 2008-10-30
I am somewhat familiar with shell scripts, we had a Unix class last year, so I can find my way around.
> **blackhole54 said:**
> 
After changing CONTROL_HD_POWERMGMT to 0 (in laptop-mode.conf), manually running the modified script gives the expected result.  That means the unmodified script should work also.  You can easily verify this
You are right, I checked and it works as expected.
> 
My belief is that copies of that script (90-hdparm.sh) exist in the following directories
Right again, files are there and cmp says they're the same.

> So if the unmodified script works (when run manually) and if it is in all of the locations I just mentioned, then I would think it should handle things correctly at start, when resuming from suspend or hibernate, and when switching to/from battery.  If it does not, I may not be able to help you troubleshoot further.
Well, everything looks right, but it doesn't work like it should.
Unmodified script works for resume but ONLY when run manually, so I think we can conclude that, for some reason, on resume from suspend it either doesn't run or if it does, somehow the APM is being reset to 128 (after the script presumably switches it to 254).

Interesting is that the same thing was happening with the 99-hdd-ugly-fix.sh in Hardy, I think I once read that other distro solved this by creating another script to make sure that the 90-hdparm.sh gets run on resume... I'll try to find that page again.
**I found a bug report about this issue (script not running on resume), the 90-hdparm.sh script needs to be copied to /etc/pm/sleep.d/**
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/244839](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/244839)
It is finally working now as it should! :)

Thank you for all your help and tips blackhole54.

---

### Post by chronniff on 2008-10-30
hmmmmm an ugly fix for the ugly fix

---

