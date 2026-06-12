---
title: "Pls Help -- can't install and Vista expires in 13 hrs"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by JohnSR on 2007-05-30
Hi,

I downloaded the Live CD and booted to it more or less successfully... there was a GNOME error message saying something along the lines of "themes will not work" (I don't remember the message exactly, but I can get it if necessary), but I was able to say OK and just keep going.  I get to the desktop alright, but when I double-click the "Install" icon, all I get is a crash message and a notification icon that disappears when I click on it for more information.  My Vista Beta license expires in about 13 hours so I need this OS to work! :)  My system details are...

Intel Pentium 4 3.06GHz w/ Hyperthreading
ASUS P4C800 Deluxe Motherboard
ATI Radeon 9800 Pro
Creative Audigy Sound Card
1 GB Corsair DDR RAM

Thanks for any help!

---

### Post by daimaru on 2007-05-30
are you using feisty ?
:-k if your already crashing with live-cd you could try choosing VESA at boot prompt (VGA) options F3 or something. and see if you can get to the desktop without errors. then after installing you can manually install the ati drivers.
forgot to ask did you check the cd for errors?

---

### Post by stevenpowers on 2007-05-30
As I am new to Ubuntu also, I can not help you with that problem. However below are the instructions for extending out your trial of Vista almost indefinitely. You will however have to do it monthly and be signed in as an administrator. I hope this helps.

he not-so-secret technique is simple: Open an elevated Command Prompt window (type cmd in the Search box, right-click the shortcut, and choose Run As Administrator from the shortcut menu). At the prompt, type slmgr.vbs -rearm and press Enter. Restart your computer. Done.
The trouble with this technique is you have to remember to do it. If the 30-day deadline passes while you're away from your computer, you'll find yourself deactivated. Here's how to handle the task automatically:
1. Click Start and type task in the Search box.
2. Click the Task Scheduler shortcut and click Continue when you see the UAC prompt.
3. In the Actions pane at the right of the Task Scheduler window, click Create Task.

4. Open a Command Prompt window (it doesn't have to be elevated), and type the command slmgr -xpr. Make a note of the date and time when the initial grace period expires.
5. On the General tab of the Create Task window, give the task a name, click Run whether user is logged on or not, and select the Run with highest privileges check box, as shown here.

6. On the Triggers tab, click New and fill in the dialog box to create a One Time task using a date and time that is before the end of the initial grace period, as calculated in Step 4. Click OK.

7. On the Actions tab, click New. The default action in this dialog box is Start a program. Fill in slmgr.vbs for the name of the program and add -rearm in the Add arguments box, as shown here. Click OK.

8. Click OK to save the task. Enter your password when prompted (this is what allows the task to approve the UAC consent request on your behalf).
Repeat this process for the second and third rearm task, making sure to choose dates that are less than 30 days after the task you just created. As long as your computer is turned on when the scheduled date and time arrive, the task will run and you'll get your renewal.

---

### Post by JohnSR on 2007-05-30
Well, after looking at other posts, I decided that it may be a good idea to try the alternate text-based installer, so I dl'd that and burned it and checksum'd it and everything.  Though it occurs to me that I didn't check it after writing it to the disk... how would you do that, exactly?

Anyway, my problem has changed.  Now the installer locks up and goes to a red screen at the "Select and install software" step.  I have a feeling that this is an important step.  As for the vista workaround, well, at this point, I've partitioned my hard drive, so I'm not really sure that I'll be able to get back to that anyway, but thanks!

Anyway, if anyone could offer some advice about this new problem, I would again be very grateful.  Thanks so far!

---

### Post by daimaru on 2007-05-30
umm sry i cant be of more help but since i dont want to reboot right now with live cd ... wasnt there a check cd for defects option at the boot screen on the live cd? try hitting F6 is it there ? otherwise i would recommend checking RAM for errors and i think that option was in the menu durring boot.
some other things.
did you try starting in safe graphics mode ? just to make sure we covered all the bases.
i mean ur pc specs seem good so i really dont see why ubuntu wont start. 
btw found something similar to your prob here [https://answers.launchpad.net/ubuntu/+question/6650](https://answers.launchpad.net/ubuntu/+question/6650) but im not sure there really is a solution cause what the guy posted at the end of the thread does not seem conclusive to me, maybe the video=vga16:off did the trick but still a radeon 9800pro should work out of the box in feisty.

oh just remembered i had a problem with an other linux distro (backtrack) way back on my laptop where if froze durring boot up (never got to desktop) solved it by passing boot parameter "acpi=off"

---

