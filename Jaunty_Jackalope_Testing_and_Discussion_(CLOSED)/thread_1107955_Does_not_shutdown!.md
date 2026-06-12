---
title: "Does not shutdown!"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2009-03-27
When I hit the shutdown button on ubuntu, I see the splash screen, but after the splash screen the screen goes black and the computer does not shutdown! Anyway to fix this?

---

### Post by tjeremiah on 2009-03-27
is anyone else having a problem with shutting down?

---

### Post by elefantcrossing on 2009-03-27
same thing happening here

---

### Post by jmore9 on 2009-03-27
Not here just ctrl+alt+del then shut down menu shows up i select what i want to do.  Shutdown, restart, etc.  Working just fine except i cannot find the shutdown button in the menu bar where it used to be , could just be me though !!

---

### Post by tjeremiah on 2009-03-27
> **jmore9 said:**
> Not here just ctrl+alt+del then shut down menu shows up i select what i want to do.  Shutdown, restart, etc.  Working just fine except i cannot find the shutdown button in the menu bar where it used to be , could just be me though !!

I see all of that but when I select shutdown, ubuntu splash screen comes up, me thinking after the splash the system will shutdown, it doesnt. :(

---

### Post by Iehova on 2009-03-27
Has it worked before on other versions of Ubuntu? I seem to recall hearing that this problem can occur if there is an ACPI error in the system as a result of the manufacturer's implementation (as opposed to an operating system problem). I'm no expert though. :oops:

---

### Post by tjeremiah on 2009-03-27
yes it did but I think I solved it. I installed the updated PYTHON from here [http://ubuntuforums.org/showthread.php?t=1107854](http://ubuntuforums.org/showthread.php?t=1107854) and the problem seems to be solved. Those that had the same problem, update PYTHON and tell me if it works.

---

### Post by tjeremiah on 2009-03-27
NOPE, I was wrong, that doesnt solve it. Still doesnt shutdown or restart.

---

### Post by matmat07 on 2009-03-27
Last thing I get is a screen with bright colored lines that slowly darkens

---

### Post by smbm on 2009-03-27
Mine sometimes hangs for several minutes with a cursor blinking in the top left. Do you have anything like that?

---

### Post by tjeremiah on 2009-03-27
> **smbm said:**
> Mine sometimes hangs for several minutes with a cursor blinking in the top left. Do you have anything like that?

yeah. It only shut down one time since I updated (stated above) but it went back to its old self. Showing a cursor blinking forever and never shutsdown.

---

### Post by Flag on 2009-03-27
I get first a scrambled screen, probably a scrambled logout screen then it turns to black and doesn't power off till I hit " enter "

---

### Post by smbm on 2009-03-27
> **tjeremiah said:**
> yeah. It only shut down one time since I updated (stated above) but it went back to its old self. Showing a cursor blinking forever and never shutsdown.

When it does that for me I just hit ctrl-alt-delete once and it seems to unfreeze things. 

That's what works for me anyway, it _may be inadvisable_ but I haven't suffered any ill effects yet.

> **Flag said:**
> I get first a scrambled screen, probably a scrambled logout screen then it turns to black and doesn't power off till I hit " enter "

I'll try just hitting enter next time I shut down/restart.

---

### Post by rburkartjo on 2009-03-27
no problems here works fine

---

### Post by elefantcrossing on 2009-03-27
after the shutdown splashscreen i get a black screen without a blinking cursor, then i just keep holding down the power-button until it really turns off. pressing ctrl-alt-del results in an reboot. 

haven't tried pressing enter yet. 

i didn't experience anything like this with the last two ubuntu versions. used to work like a charm.

---

### Post by smbm on 2009-03-27
> **elefantcrossing said:**
>  pressing ctrl-alt-del results in an reboot.

Good point, I hadn't thought of that, I seldom shut down so I was just saying how I unfreeze things. I should start to think before I post more.

---

### Post by tjeremiah on 2009-03-27
> **elefantcrossing said:**
> after the shutdown splashscreen i get a black screen without a blinking cursor, then i just keep holding down the power-button until it really turns off. pressing ctrl-alt-del results in an reboot. 

haven't tried pressing enter yet. 

i didn't experience anything like this with the last two ubuntu versions. used to work like a charm.

yea, this has never happened before. Strange :(

---

### Post by seppl82 on 2009-03-28
Hi,

i have the same issue here.
If i go to shutdown i get s scrambled screen and the Notebook doesn't turn of. If i press the poweroff button nothing happens if i press return nothing happens and ctrl alt delete does nothing too.
The only way to turn it of it the hard off.
In Intrepid and Hardy it worked fine.

The Problem started with the update to Jaunty.

Kind Regards
Seppl

---

### Post by 4Orbs on 2009-03-28
This has worked for me ever since I first started using Ubuntu (Gutsy). It has worked on every Ubuntu and Ubuntu spinoff I have installed (dozens) over the past year.

First open the /etc/modules file in the text editor as root:
```
gksudo gedit /etc/modules
```
Then add this text as the last line in the file:
```
apm power_off=1
```
Save the file and close it.

Then reboot (important) and shutdown should work correctly thereafter. I don't understand why Ubuntu, Mint, CrunchBang and the other Ubuntu based distros have never included this fix. I know from following the forums that it works for many users with the shutdown problem, but not all of 'em.

---

### Post by WiFi Ed on 2009-03-28
> **4Orbs said:**
> This has worked for me ever since I first started using Ubuntu (Gutsy). It has worked on every Ubuntu and Ubuntu spinoff I have installed (dozens) over the past year.

First open the /etc/modules file in the text editor as root:
```
gksudo gedit /etc/modules
```
Then add this text as the last line in the file:
```
apm power_off=1
```
Then reboot (important) and shutdown should work correctly thereafter. I don't understand why Ubuntu, Mint, CrunchBang and the other Ubuntu based distros have never included this fix. I know from following the forums that it works for many users with the shutdown problem, but not all of 'em.

I've been having this problem on my notebook with Jaunty (desktop works ok) and your suggestion fixed it for me. Thanks!:)

Edit: Hmmm, it WAS working at first, but it still hangs up. Oh well....

---

### Post by tjeremiah on 2009-03-28
> **WiFi Ed said:**
> I've been having this problem on my notebook with Jaunty (desktop works ok) and your suggestion fixed it for me. Thanks!:)

Edit: Hmmm, it WAS working at first, but it still hangs up. Oh well....

LOL, same. This problem isnt going away :(

---

### Post by seppl82 on 2009-03-30
Anyone want's to open a bug ticket for that issue?

---

### Post by tjeremiah on 2009-03-30
> **seppl82 said:**
> Anyone want's to open a bug ticket for that issue?

I have trouble reporting bugs. Hopefully someone with the same problem can in detail.

---

### Post by seppl82 on 2009-03-30
Hey,

different Question to all.
I've tried to hibernate the Notebook (Memorydump to HDD).
Amazingly the Notebook did the "Power off" without any problems.

Colleagues could you confirm that?

Kind Regards
Seppl

---

### Post by tjeremiah on 2009-03-30
> **seppl82 said:**
> Hey,

different Question to all.
I've tried to hibernate the Notebook (Memorydump to HDD).
Amazingly the Notebook did the "Power off" without any problems.

Colleagues could you confirm that?

Kind Regards
Seppl

Just did it and it hangs, cursor on top blinking and does nothing. Had to hold the power button to shutoff.

---

### Post by seppl82 on 2009-03-30
Hey,

i've found something amazing.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332772](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/332772)

Take a look on this bug.
I've changed the entry in menu list and removed quiet and splash and added vga=791

And it's working.

Please add your opinions to the bug shown above to increase the priority!

---

### Post by linuxaz on 2009-03-30
Oh, yes please add comments.....  Thanks for finding it... I think.

mckeeshop

---

### Post by seppl82 on 2009-03-31
Could the others confirm that the workaround from the listed launchpad bug works for you too?

Kind Regards
/Seppl

---

### Post by tjeremiah on 2009-03-31
> **seppl82 said:**
> Could the others confirm that the workaround from the listed launchpad bug works for you too?

Kind Regards
/Seppl

it didnt work.

---

### Post by loomsen on 2009-03-31
Experienced this problem in earlier releases too, for me it seems to depend on whether the current user has explicit authorizations to do foo or bar.

Like, if I have a USB-disk attached, which was mounted auto (by root), it doesn't work. If I mount it in userspace, or grant explicit authorizations to the user to reboot the system/unmount FSs mounted by other users/whatever it works.

Try configuring your polkit and see if it changes.

---

### Post by seppl82 on 2009-03-31
As far as i understood the problem described in this thread is that the machine goes down for shutdown but does not turn off.

Did i understood this right?

Does this realy apply to user rights???

---

### Post by tjeremiah on 2009-03-31
> **seppl82 said:**
> As far as i understood the problem described in this thread is that the machine goes down for shutdown but does not turn off.

Did i understood this right?

Does this realy apply to user rights???

I dont know about user rights but yes, the pc goes for shutdown and does not shutdown.

---

### Post by seppl82 on 2009-03-31
Did you see the splash screen after booting and adaption of your menu.lst.

My first mistake was that i've removed the splash entry in the parameters above and not in the boot options below.

---

### Post by elefantcrossing on 2009-03-31
here shutdown started working again

i think my wireless card (iwlagn4965) was keeping my computer from shuting down
it started to work after i switched to the linux-backports-modules

---

### Post by loomsen on 2009-03-31
[[img]http://www.ubuntu-pics.de/thumb/11774/screenshot_028_2ytJFM.png[/img]](http://www.ubuntu-pics.de/bild/11774/screenshot_028_2ytJFM.png)

[[img]http://www.ubuntu-pics.de/thumb/11775/screenshot_029_cbMFn7.png[/img]](http://www.ubuntu-pics.de/bild/11775/screenshot_029_cbMFn7.png)

As you may be able to see, there are some tasks which require admin authentication.

Bear in mind, unix is a multi (which can mean many) user system, it's trivial if you're the only user of your system. But if you imagine one actual CPU and many terminals to log in, would u like it if I chose to reboot while you're working on another terminal?

But actually, I guess your right, keep guessing...

---

### Post by seppl82 on 2009-04-01
Hi loomsen,

as far as i see this rights demonstrate the shutdown process. (If the user is allowed to shutdown or Reboot the PC).

In our case the PC shuts down without any problem. But it stucks at the poweroff sequence (end of the shutdown).

**tjeremiah: Do you see a splash screen on Boot time?**

Kind Regards
/Seppl

---

### Post by tjeremiah on 2009-04-01
> **seppl82 said:**
> Hi loomsen,

as far as i see this rights demonstrate the shutdown process. (If the user is allowed to shutdown or Reboot the PC).

In our case the PC shuts down without any problem. But it stucks at the poweroff sequence (end of the shutdown).

**tjeremiah: Do you see a splash screen on Boot time?**

Kind Regards
/Seppl

sorry for the late response but yes, I see the splash screen. But I believe I have good news, the problem appears to be solved since a update I did yesterday afternoon :)

---

### Post by ormandj on 2009-04-01
I had the same issue, and it also was resolved as of updating today. I've seen it before, it shows up from time to time, same exact symptoms you described.

Lenovo T400, Intel GFX and WLAN.

---

### Post by sgosnell on 2009-04-01
This is a known problem with some wireless cards, and with some sound cards.  The cards don't shut down properly and thus don't allow the laptop to shut down.  The wiki has fixes for these, and the exact fix will depend on the make and model of computer.

---

### Post by phenest on 2009-04-03
I don't use my wireless, but I disabled in Network Manager, and the computer shuts down fine. With it enabled, it hangs. Never had this problem before.

---

### Post by tjeremiah on 2009-04-04
I was wrong. The other day, the update did not solve the problem.

---

### Post by WiFi Ed on 2009-04-04
> **loomsen said:**
> [[img]http://www.ubuntu-pics.de/thumb/11774/screenshot_028_2ytJFM.png[/img]](http://www.ubuntu-pics.de/bild/11774/screenshot_028_2ytJFM.png)

[[img]http://www.ubuntu-pics.de/thumb/11775/screenshot_029_cbMFn7.png[/img]](http://www.ubuntu-pics.de/bild/11775/screenshot_029_cbMFn7.png)

As you may be able to see, there are some tasks which require admin authentication.

Bear in mind, unix is a multi (which can mean many) user system, it's trivial if you're the only user of your system. But if you imagine one actual CPU and many terminals to log in, would u like it if I chose to reboot while you're working on another terminal?

But actually, I guess your right, keep guessing...


Thanks loomsen! I changed the authorizations setting for "Unmount file systems mounted by other users" (shown in the top pic in your post) to "Yes" for "Anyone" and "Console" and now restart and shutdown seem to be working properly.:guitar:

Edit: Aaaargh! Spoke too soon. After several successful restarts/reboots it is once again hanging at "Killing all remining processes..." [fail] and "Unmounting local filesystems..." mount: / is busy.

Edit #2: I posted to this bug at Launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/350207]("https://bugs.launchpad.net/ubuntu/+bug/350207")

---

### Post by loomsen on 2009-04-07
> **WiFi Ed said:**
> Thanks loomsen! I changed the authorizations setting for "Unmount file systems mounted by other users" (shown in the top pic in your post) to "Yes" for "Anyone" and "Console" and now restart and shutdown seem to be working properly.:guitar:

Edit: Aaaargh! Spoke too soon. After several successful restarts/reboots it is once again hanging at "Killing all remining processes..." [fail] and "Unmounting local filesystems..." mount: / is busy.

Edit #2: I posted to this bug at Launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/350207]("https://bugs.launchpad.net/ubuntu/+bug/350207")

Check your hdparm settings too. If you have your Data flushed only every i.e. 5 secs this may cause those hangers too. 

However, would be more interesting to know which process wasn't killed, as this is more likely to be the bug (filesystems can't be unmounted while there are still processes running)

Glad you had a small success at least tho :)

---

