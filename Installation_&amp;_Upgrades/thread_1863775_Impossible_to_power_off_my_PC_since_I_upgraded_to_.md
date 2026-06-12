---
title: "Impossible to power off my PC since I upgraded to 11.10"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by pascalchap on 2011-10-18
I am using a mother board ASUS M4A89GTD PRO/USB3 with an AMD Phenom6.

I was using Ubuntu 11.04 64 bits without problem, except some issue while using Sculptris under Wine.

I upgraded to 11.10 64 bits with a weak dream that it could solve this. The process looked OK until the final restart when I had some trouble with some message like "configuring the network failed". I changed the Ethernet cable from my PCI board to the integrated connection and it started.

I didn't make an exhaustive test, neither performance test, but everything I have tested seems OK.

The problem is that my PC does not shutdown. The sessions stops, I get the usual black screen with some information, but after 1 second, it returns to the login screen, and then the shutdown command seems to have no effect.

It is still possible to open a new session.

I used the hardware shutdown (2 seconds on power ON/OFF) But when I restart I needed several trials to succeed (another configuring network issue, boot frozen...).
Is there something I can try to solve this, before I go back to 11.04?

**Some more information:**
I used the command "sudo shutdown -h -P now" from a console, and the PC shut down very quickly. Maybe too quickly because when I start it up again, I got the usual setup screen, a useless flashing information screen, and got stuck before the Ubuntu 5 dots appear. I have wait a few minutes without success, then reset the board with the HW button. The boot stopped in the Grub screen, asking to select a linux version. I choose the latest one, and Ubuntu 11.10 finally wake up. Even my XP laptop has better operating modes :o)


Thanks.

---

### Post by changtraidoc on 2011-10-20
I have a trouble like this, any one here can help us :(

---

### Post by pascalchap on 2011-10-25
Nothing new? If some one can suggest some test to do, or report I could give, please tell me. This problem occurs when no user session is active so I don't know what to do, but staring at my frozen screen ...
Seriously, I can use hibernate function (not 100% working) or use the hardware power off, but even if I do it while all sessions are closed, I am not very confident doing this 2 a 3 times a day.

Pascal

---

### Post by airplanesimen on 2011-10-25
okay... i had the same problem with my linux for a while. is the same thing happening when you only type  "sudo halt"  in your terminal?

---

### Post by airplanesimen on 2011-10-25
you should check this out first:

[http://ubuntuforums.org/showthread.php?t=1466589&page=1](http://ubuntuforums.org/showthread.php?t=1466589&page=1)

Same issue, maybe helps?

---

### Post by pascalchap on 2011-10-25
As I said, sudo shutdown -h -P now succeed to power off but I am in trouble with restart.

I am going to try the halt now, I'll tell you tomorrow the result - it is time to sleep here.

Pascal.

---

### Post by airplanesimen on 2011-10-25
> **pascalchap said:**
> As I said, sudo shutdown -h -P now succeed to power off but I am in trouble with restart.

I am going to try the halt now, I'll tell you tomorrow the result - it is time to sleep here.

Pascal.

okay :P

Are you troubelin' with restarting your pc by pressing that power off key at your logon screen?? (btw: Restart command in terminal is "reboot" or "sudo reboot"). tell me tomorrow, good night!

---

### Post by nlucaroni on 2011-10-25
[FONT="Courier New"]halt[/FONT] is just invokes for either [FONT="Courier New"]reboot[/FONT] or [FONT="Courier New"]shutdown[/FONT] or [FONT="Courier New"]poweroff[/FONT] depending on the arguments passed.

I had no problems using any of the commands above on my 11.10 --just a ton other :-/

---

### Post by airplanesimen on 2012-01-12
It could be that you don't have the APM module loaded. Do the following:

1. Change to root and open the file /etc/rc.d/rc.modules
2. Look for the part that's headed "APM support" (in my file, it's near the top)
3. If you see the line #/sbin/modprobe apm, delete the # and save the file.

I think you'll have to restart (if u can) your machine for the changes to take effect.
got it from here: [http://www.linuxquestions.org/questi...estart-341832/](http://www.linuxquestions.org/questi...estart-341832/)
__________________
-------------------------------------------------------------------

---

### Post by arvevans on 2012-01-18
There are reports all over the Internet about laptops that used to shutdown fine in Ubuntu 11.04 but now will not shutdown properly in 11.10 release.  It apparently is a serious bug because so may people are complaining about it.  It apparently is not specific to any one brand or model of laptop, although some do seem to not have the problem.  Some web sites claim that it is a bug in the latest kernel not properly killing video interfaces, but I'm not so sure.  Some also claim that going back one version in the kernel fixes the problem.  That didn't work for me.

My own Toshiba laptop would shutdown fine using 11.04 but now hangs in the last stage of shutdown with 11.10 Ubuntu.  Forcing it down with the power switch only takes it to hibernate mode.  Then I have to push the hidden  reset button to make it boot properly at the next power up.

---

### Post by airplanesimen on 2012-01-19
> **arvevans said:**
> There are reports all over the Internet about laptops that used to shutdown fine in Ubuntu 11.04 but now will not shutdown properly in 11.10 release.  It apparently is a serious bug because so may people are complaining about it.  It apparently is not specific to any one brand or model of laptop, although some do seem to not have the problem.  Some web sites claim that it is a bug in the latest kernel not properly killing video interfaces, but I'm not so sure.  Some also claim that going back one version in the kernel fixes the problem.  That didn't work for me.

My own Toshiba laptop would shutdown fine using 11.04 but now hangs in the last stage of shutdown with 11.10 Ubuntu.  Forcing it down with the power switch only takes it to hibernate mode.  Then I have to push the hidden  reset button to make it boot properly at the next power up.
The only thing i know, is that it will be a BIG update soon, fixing some bugs in unity and Ubuntu itself. maybe u should wait until then? i dont know when it is coming, but i think it is just around the corner :P

---

