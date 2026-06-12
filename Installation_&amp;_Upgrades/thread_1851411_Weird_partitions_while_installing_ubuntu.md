---
title: "Weird partitions while installing ubuntu"
date: 2011-09-28
forum: Installation &amp; Upgrades
---

### Post by WannabeFantasma on 2011-09-28
Hi all

Today my sister brought her laptop to me to install it Windows 7 and then install ubuntu after it, I created a 15gb partition for ubuntu, and alot of space for her files see:

[http://imageshack.us/f/402/paries.jpg/](http://imageshack.us/f/402/paries.jpg/)

now when I want to install ubuntu, I see this:

[http://imageshack.us/f/171/pariesubuntu.jpg/](http://imageshack.us/f/171/pariesubuntu.jpg/)

[http://imageshack.us/f/717/pariesubuntuhandmatig.jpg/](http://imageshack.us/f/717/pariesubuntuhandmatig.jpg/)

How can I fix this so I can install ubuntu on the right partition?

I've never seen something like this.

Hope you guys can help me!

Wannabe

---

### Post by Beacon11 on 2011-09-28
You may get more help if it wasn't all in... what is it... German?

It looks like your partitions are in a state straight from the manufacturer, but I got the impression this was a clean Windows 7 install. If I were you, I'd wipe the whole thing and start fresh, getting rid of all the extra partitions you have on there. If you have an Windows 7 disk, you don't really need the restore partition, do you?

---

### Post by Quackers on 2011-09-28
Your Windows partitions have become Dynamic Discs. This is often caused by an attempt to create a 5th primary partition. Whilest Windows is fine with these partitions Linux cannot install as it can't "see" the dynamic discs.
It may be necessary to re-install Windows then look to see how many primary partitions are being used. If that number is 4 then one needs to be deleted then an extended partition can be created which can hold as many logical partitions as you want. 
Ubuntu can boot from a logical partition but Windows cannot (normally).

There may be another way. You can try the method given in this thread to convert the dynamic discs back to basic partitions. 

[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

Recently some hardware manufacturers have taken to using all 4 primary partitions (which is the maximum on a MBR partitioned disc).

If that's teh case you can write to them telling them what you think :-)

---

### Post by WannabeFantasma on 2011-09-28
@Beacon11 it's Dutch :D
Bestanden = Files
Ubuntu = Where ubuntu has to come
Recovery = HP recovery partition
System = something with win7
HP tools = ???
De witte (The White One) = My usb drive to get the screenshots on :D

I'll try to fix partitions :D 


now I even have a bigger problem though... recovery mode won't work... and can't write backup disk since i dont' have the battery for it... ah well let's see what we can fix here :D

---

### Post by Quackers on 2011-09-28
Are you running recovery from the pre-installed partition, with a key press during boot?
That should work.

---

### Post by Beacon11 on 2011-09-28
> **WannabeFantasma said:**
> @Beacon11 it's Dutch :D
Bestanden = Files
Ubuntu = Where ubuntu has to come
Recovery = HP recovery partition
System = something with win7
HP tools = ???
De witte (The White One) = My usb drive to get the screenshots on :D

I'll try to fix partitions :D 


now I even have a bigger problem though... recovery mode won't work... and can't write backup disk since i dont' have the battery for it... ah well let's see what we can fix here :D

Oh! I am 1/4th Dutch and can't recognize it. Can I say it's CLOSE to German :P ? I updated my first post before I realized there were several subsequent posts, sorry about that. Can you clarify whether the laptop had Windows 7 on it already or if you put it on there yourself?

---

### Post by WannabeFantasma on 2011-09-28
it came with Winows 7 pre installed
+ the recovery partition...

I do not have the DVD to just re-install the laptop all over again + i can't make one since you need a battery for that? :/

when i press F11 to repair windows  it says :

```
Windows failed to start. A recent hardware or software change might be the cause.

File: \Boot\BCD
Status 0xc0000225

An error occurred while attempting to read the boot configuration data.
```

so yeh i'm pretty much stuck now :/

---

### Post by Quackers on 2011-09-28
Are you intending to re-install Windows from the recovery partition?

---

### Post by WannabeFantasma on 2011-09-28
Yes that's what i wanted to do, but seems like its not working because of that error...

Restart
I press F11 to get into recovery mode
(i have the recovery cd but i can't recover from the recovery partition?)
then i get: 
> Windows failed to start. A recent Hardware or software change might be the cause. To fix the Problem:

1. Insert your Windows installation disc and restart your computer
2. choose your language settings, and then click "next"
3. Click "repair your computer."

If you do not have the disc, contact your system administrator or computer manufacturer for assistane

File: \Boot\BCD
Status: 0xc0000225
Info: An error occurred while attempting to read the boot configuration data

---

### Post by Quackers on 2011-09-28
I don't have a HP system but from memory isn't F10 the key to press for recovery?

Please be aware that running the recovery partition will wipe out everything on the system - including all data - and return the system to the state it was in on the day you bought it.

---

### Post by WannabeFantasma on 2011-09-28
F11 for me not working (see above)

i have made 1 disk.. a systemrecoverydisc but it doesn't seem to be working.

trying to get the bcd thing to work :D

tried [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) still not working :/

---

### Post by Quackers on 2011-09-28
I did see the above. That's why I suggested F10 :-)

---

### Post by WannabeFantasma on 2011-09-28
> **Quackers said:**
> I did see the above. That's why I suggested F10 :-)

Ah ok F10 = Bios :D

---

### Post by Quackers on 2011-09-28
I see. It sounds like F11 is not booting (or not trying to boot) the recovery partition. Or alternatively the recovery partition is damaged. Do you have the manual for that pc? Have a look if there is a different key sequence for starting recovery.

---

### Post by WannabeFantasma on 2011-09-28
Well earlier right after the resizing we could get into recovery mode with F11, for some reason it suddenly broke.


I reformatted all the partitions i made and stuck it back to the normal C:

might just order HP recovery disks since it looks like i screwed everything up :/

---

### Post by Quackers on 2011-09-28
While you're speaking to HP you can tell them that their current policy of using all 4 primary partitions had a hand in causing your problems! Do some screaming and see if they'll send you some recovery discs for free :-)
And when the system is recovered please make a set of recovery dvd's and a repair disc. Both easily done from within Windows!

---

### Post by WannabeFantasma on 2011-09-28
Or I could just use another cd key I can get from academic dowload... 

Recovery partitions are weird...

+ Systemrecoverydisc won't actually do anything... :/

---

### Post by Quackers on 2011-09-28
They are, that's why it's imperative to make recovery dvd's. It's the first thing I do with a new computer and I run it twice to different types of dvd (if permitted).
It would really upset me to have to buy them from the manufacturer :-)
They should be supplied with a new pc but the manufacturers like to save the few pence a dvd costs!

---

### Post by WannabeFantasma on 2011-09-28
i know we planned to do that than we figured out you had to have the battery for the laptop (she didn't brought it with her) 

Next time i'm sure i will do that before everything else :D  (Or say to get the laptop from real pc store here where you just need receipt + laptop cd key to get the recovery dvd for free!)

Trying to make a backup with windows now see what that does... :D

Thanks for all the help!
So next time i don't make dynamic disks... well probably next time everything will just be like every other time I installed dual boot Win/Ubuntu... :D

---

### Post by srs5694 on 2011-09-28
You can get standard Windows 7 installation discs from the [My Digital Life site.](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/) The claim is that these images are approved by Microsoft. A few caveats:


[list]
[*]Not all languages are available -- they seem to have English, German, French, and Spanish for the most common varieties.
[*]You'll need your current license key. It's usually printed on a sticker on the computer. If you can't find such a sticker or if it's torn off, you'll need to get it from the Windows Control Panel. (I don't recall exactly where.)
[*]Be sure to get the version that you've already got on the computer. Your license key will only be good for that version.
[*]These discs will install the standard version of Windows. You'll lose any custom software or drivers that might be provided with the installation on your computer. Sometimes this isn't a big loss, but other times you might need to go hunting for drivers or give up useful software.
[/list]

---

### Post by WannabeFantasma on 2011-09-29
Installed the academic downloads version, dual-boot works fine now!

(except for keyboard under ubuntu but that's another thread :D )

---

### Post by Quackers on 2011-09-29
How strange!

---

