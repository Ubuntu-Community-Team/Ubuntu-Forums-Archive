---
title: "Rebuild status raid 1 intel isw fakeraid intel"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by cberni on 2010-10-01
I have recently installed Ubuntu 10.04.1 lts server on my Intel "fakeraid" (software raid)  (2x250 sata).

To test my RAID 1 I turned off one HD and start the system.

The first screen (Intel software screen) show Status = Degraded, but the system starts normally with just one HD.

Then  I turned off the system and turned on the HD again, so the first screen  (Intel software screen) shows Status = Rebuild. If I enter in the  software raid panel the folowing message is showed: "Volumes with  "Rebuild" status will be rebuilt within the operating system"

The system starts normally... but this message status stays permanently even I restart the system again.

How could I rebuild the raid to get Status = Normal again??

---

### Post by psusi on 2010-10-01
You need to not restart the system until it has finished copying the drive.

Actually I'm not even sure that rebuilding is supported for fake raids.  Unless you are dual booting with windows, you should not use the fake raid.  Delete the array in the bios, and reinstall using software raid.

---

### Post by cberni on 2010-10-01
"You need to not restart the system until it has finished copying the drive."

nothing is started to copy... just the status stays as Rebuild.


"Actually I'm not even sure that rebuilding is supported for fake raids.   Unless you are dual booting with windows, you should not use the fake  raid."

I'm not using windows, just Ubuntu 10.04.1 lts **server**.


"Delete the array in the bios, and reinstall using software raid."

Delete the array and reinstall all the server system in production is not a good idea. Should be a option to just rebuild the raid.

---

### Post by psusi on 2010-10-01
You put the server into production and THEN decided to test if it would work without one disk?  That's not a good idea.

---

### Post by cberni on 2010-10-01
NO! is not in production, but I'm simulation if it was.
I would like a option to rebuild and not install all again.

If I type **dmraid -s** I get the following:
--> Active Subset
name : isw_bdfgcfeibe_inovati
size : 488390912
striade : 128
type : mirror
**status : nosync**
subsets : 0
devs : 2
spares : 0

before the test (before turn off a HD): **status : ok**
during the HD was turned off: **status : inconsistent **
after turn on the HD: [B]status : nosync
[/B]
How could I get **status : ok **again?

---

### Post by psusi on 2010-10-01
I must not have been clear.  I don't think dmraid supports resyncing the array.  It is not a well supported tool and you will avoid a lot of problems if you do not use it, which is why I said you should delete the raid arrays and reinstall using plain old software raid.

---

### Post by cberni on 2010-10-01
Oh God, I can't believe that. If one HD fails must have a option to just put a new HD and sync the data to have raid 1 (mirror) again (not create the array and install all the system).

Is the life so hard? Anybody knows another way?

---

### Post by psusi on 2010-10-01
> **cberni said:**
> Oh God, I can't believe that. If one HD fails must have a option to just put a new HD and sync the data to have raid 1 (mirror) again (not create the array and install all the system).


You CAN, just not with fake raid.  You need to use regular software raid for that.

---

### Post by cberni on 2010-10-01
But the fakeraid says at the first screen page after turn on button:  "Volumes with  "Rebuild" status will be rebuilt within the operating system"

Must have a solution...

---

### Post by psusi on 2010-10-01
The solution is to stop using the fake raid and switch to software raid.

---

### Post by cberni on 2010-10-03
Is fakeraid not software raid?? (i thought fakeraid = software raid)

---

### Post by ronparent on 2010-10-03
Fakeraid is basically software raid that uses a MB raid chipset to help set up the raid. In Windows you are required to install a 'driver' to use the raid, but, it is otherwise transparent to the user and relatively easy to use. In a linux OS purpose of the driver equivalent is served by a program called dmraid which activates the raid for use. It essentially functions like a software raid but isn't strictly as defined within Linux in general. That is your only resort if you want your raid partitions accessible to both windows and ubuntu.

If, however, you use only Ubuntu (or any other linux distro) you can setup a linux based pure software raid. That is accomplished using a linux program called mdadm. That requires a little more knowledge to set up but is just as easy to use. Both have quirks which vary from between each Ubuntu version but are otherwise functional. Neither is appropriate to a relatively uninformed user without some study.

---

### Post by cberni on 2010-10-03
I use only Ubuntu and I want to setup a linux based pure  software raid.
Do you have any tip how could I do that? (install the mdadm seems easy with apt-get install, but how to configure that)
Another question is how could I know if a HD has failed?

---

### Post by psusi on 2010-10-03
You have to install Ubuntu using the alternate cd.  The text mode installer can build software raids and install to them.  First you need to destroy the fake raids in your bios.  You can set up mdadm to email you if a disk fails.  In fact, it is set up to email root by default; you just need to install a mail server.

---

### Post by ronparent on 2010-10-04
Additionally you should erase any fakeraid meta data on any disk previously configured in a fakeraid and then remove dmraid.

---

### Post by psusi on 2010-10-04
> **ronparent said:**
> Additionally you should erase any fakeraid meta data on any disk previously configured in a fakeraid and then remove dmraid.

Hence the "First you need to destroy the fake raids in your bios" comment.  Once that's done there is no reason to remove dmraid; it won't do anything without the fakeraid meta data around.

---

### Post by cberni on 2010-10-05
ok... I'll not setup a linux based pure  software raid anymore.

The "fakeraid" intel and dmraid seems work fine.
Please, look this link: [http://techie.org/Blog/2010/09/03/how-to-rebuild-intel-raid-isw-on-linux/](http://techie.org/Blog/2010/09/03/how-to-rebuild-intel-raid-isw-on-linux/)

Right away after reboot with the second HD turned on again if I type **sudo dmsetup status**     I got:

isw_eacifcfchi_inovati5: 0 19873792 linear      
isw_eacifcfchi_inovati1: 0 468512768 linear      
isw_eacifcfchi_inovati: 0 488390920 mirror 2 8:0 8:16 **_*928/3727*_** 1 AA 1 core

And after long time if I type it again I get the same result as the system has recently installed with the fakeraid1 **normal**:

isw_eacifcfchi_inovati5: 0 19873792 linear      
isw_eacifcfchi_inovati1: 0 468512768 linear      
isw_eacifcfchi_inovati: 0 488390920 mirror 2 8:0 8:16 **_*3712/3727*_** 1 AA 1 core

BUT if I type **dmraid -s** I get the following:
--> Active Subset
name : isw_bdfgcfeibe_inovati
size : 488390912
striade : 128
type : mirror
**status : nosync**
subsets : 0
devs : 2
spares : 0

This **status : nosync** remain. If I reboot the system the fakeraid status remain **rebuilt **status and if I type **sudo dmsetup status**     I got:

isw_eacifcfchi_inovati5: 0 19873792 linear      
isw_eacifcfchi_inovati1: 0 468512768 linear      
isw_eacifcfchi_inovati: 0 488390920 mirror 2 8:0 8:16 **_*50/3727*_** 1 AA 1 core

(The progress is started again.)

Nobody knows how could I get **status : ok** again in dmraid??

---

### Post by psusi on 2010-10-05
> **cberni said:**
> ok... I'll not setup a linux based pure  software raid anymore.

The "fakeraid" intel and dmraid seems work fine.
Please, look this link: [http://techie.org/Blog/2010/09/03/how-to-rebuild-intel-raid-isw-on-linux/](http://techie.org/Blog/2010/09/03/how-to-rebuild-intel-raid-isw-on-linux/)

No, that is what you have BEEN using, which is fake hardware raid.  You need TO use pure software raid.

---

### Post by cberni on 2010-10-05
Yes, but isn't there a way to get **status : ok** again in dmraid using fake hardware raid?

---

### Post by cberni on 2010-10-05
please look this link: [http://techie.org/Blog/2010/09/03/ho...-isw-on-linux/]("http://techie.org/Blog/2010/09/03/how-to-rebuild-intel-raid-isw-on-linux/")
is exactly my problem, but I don't get the **status : ok** again.[]("http://techie.org/Blog/2010/09/03/how-to-rebuild-intel-raid-isw-on-linux/")

---

### Post by psusi on 2010-10-05
> **cberni said:**
> Yes, but isn't there a way to get **status : ok** again in dmraid using fake hardware raid?

No.

dmraid is not a well tested or supported tool.  It is only provided for those who need to dual boot with Windows, since Windows does not understand Linux software raid, and Linux does not understand Windows software raid.

mdadm Linux software raid is far better tested and supported.  You will have much fewer problems with it, and it also will resync much faster when you plug the missing drive back in, so you should use that instead of dmraid.  It also can do things like add a third disk later on if you want, which you can not do with the fake raid stuff.

---

