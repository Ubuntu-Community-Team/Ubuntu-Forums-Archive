---
title: "Solution: Ubuntu (Wubi) won't uninstall. bcdedit entry error."
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by Scott.57215 on 2010-03-20
[COLOR=Red]**Please take extreme care while following my solution.**[/COLOR]

I have been playing around with Ubuntu and Windows lately and I gave Wubi a shot. When I decided to uninstall Ubuntu (Wubi), I was given the error that the uninstaller couldn't delete the entry from bcdedit.exe as it was missing.

[IMG]http://img405.imageshack.us/img405/681/wubiuninstallfix1.jpg[/IMG]

I had manually deleted the boot entry myself before-hand by accident and therefore made a mistake. The way I managed to get around this was fairly simple. I'm going to share my solution with you.

**Step 1:** Try and uninstall Ubuntu via Wubi and note down the part of the error shown in the image above.

**Step 2:** Download EasyBCD 2.0 ([Google]("http://www.google.co.uk/#hl=en&q=EasyBCD+2.0")), install it and create a boot entry. To do this, launch EasyBCD and goto Add/Remove Entries. Now click the Linux/BSD tab and set the Type to "Wubi" and give it the name "Ubuntu". Finally, click "Add Entry".

[IMG]http://img704.imageshack.us/img704/7269/wubiuninstallfix2.jpg[/IMG]

**Step 3:** Now close EasyBSD and enter "cmd.exe" in the Windows search box on the start menu. Right click cmd.exe and select "Run as Administrator". Now, type "bcdedit.exe" into the Command Prompt window and hit enter.

It will spew a lot of writting into the Command Prompt but we want the end of it (Real-mode Boot Sector). Find the entry named "Ubuntu" and note down the identifier.

[IMG]http://img339.imageshack.us/img339/6144/wubiuninstallfix3.jpg[/IMG]
[B]
Step 4:[/B] Close cmd.exe and now search for "regedit.exe" the same way as we did cmd.exe. Now goto Edit > Find and then search for the bit of text we took note of in the error at the beginning.

If all is well you should get a screen like the one shown below. We are going to edit the "VistaBootDrive" entry. Right click on it and select "Modify". Now delete the text shown in the box and replace it with the identifier you took note of from the Command Prompt earlier and click OK.

[IMG]http://img249.imageshack.us/img249/162/wubiuninstallfix4.jpg[/IMG]

**Step 5:** Now attempt to uninstall Ubuntu via Wubi again and all should be well.

[IMG]http://img443.imageshack.us/img443/605/wubiuninstallfix5.jpg[/IMG]

I hope this has helped you :D. Now go and install Ubuntu [B]for real!
[/B][SIZE=1]
You may copy this solution and publishit  on your blog/website but please link back to the original one here.[/SIZE]

---

### Post by dstar on 2010-03-27
Thanks for the guide but it does not seem to be working with windows 7 and EasyBCD2.0 build 90


[IMG]http://img404.imageshack.us/img404/245/errorv.png[/IMG]


[IMG]http://img176.imageshack.us/img176/1000/cmd.png[/IMG]
Shot at 2010-03-27
[IMG]http://img260.imageshack.us/img260/6678/regedit.png[/IMG]

---

### Post by Scott.57215 on 2010-03-28
Have you tried searching regedit.exe until you find VistaBootDrive on the right? You may need to use "Find Next" until you find it.

**EDIT:** I noticed you searched for the identifier from the Command Prompt and not the identifier from the error message. Try search for "723ed23**a**-140e-11df-84cb-a1e8bb1b8261" without the quotes. Notice the a and not the b.

---

### Post by garvinrick4 on 2010-03-28
To remove an entry from bcdedit in Vista or 7.

Code: bcdedit delete {   indentifier number  }


So find the one with wubblder or something close to that and that is the on that attached itself
to the Windows boot manager and run that code and it is gone.

Happens sometimes when a user uses ADD and REMOVE programs to delete a WUBI install instead of using the uninstall in the WUBI folder in C: drive like they are suppose to. No big
deal that is how I learned at one time by goofing it up.

---

### Post by LonelySEason on 2010-09-24
Hi can u take few minutes and look at this one [http://ubuntuforums.org/showthread.php?t=1577524](http://ubuntuforums.org/showthread.php?t=1577524)
This is my Ubuntu installation error.
Any help will appreciate.

PS. I believe it's relative to bcdedit entry but don't know how to solve it.

---

### Post by Styked on 2011-01-17
Having the same problem as dstar. searching for both the initial error text and the text from the cmd brings the same screen up in regedit. And by the way, i'm running windows 7, can anybody please help? formatting didn't solve this problem, no luck till now...

---

### Post by tinkernutfan on 2011-02-21
thank you so much minecraft stopped working on my windows 7 so i needed to fix ubuntu because im useing all my partitions

---

### Post by illutian on 2012-03-03
FYI: Someone needs to reupload the wubiuninstallfix4.jpg image. It's no longer on Imageshack.

---

### Post by oldos2er on 2012-03-03
Closed, necromancy.

---

