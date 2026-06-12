---
title: "Total Newbie with display issues"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by mburman23 on 2011-09-22
I'm stumped... I am installing lubuntu on an older pc. It's a pIII with s3 trio 32/64 graphics card and a sasmsung syncmaster 151v display. It boots up ok but only the top half of my display is "on". I can't see anything below the half-way point! I tried to install a driver specific to the s3 card (not sure how successful I was at that) but it didn't seem to help. I haven't a clue how to trouble shoot this... especially since I can't see the bottom half of the screen. In "command prompt" I have full display but I don't know how to use linux from the command line.
 
Any help is greatly appreciated!
 
Michael

---

### Post by squenson on 2011-09-22
First test (FULLY read this message as you won't see it while you run the test! REMEMBER THE STEP 5 ( Ctrl-Alt-F7 ) IN CASE YOU ARE LOST WITH A BLACK SCREEN!):

    1. Press Ctrl-Alt-F4 to get to a terminal mode
    2. Login using your usual user-id and password
    3. Type the command ls several times, just to see if the full screen is working
    4. Logoff with the command Exit
    5. Press Ctrl-Alt-F7 to get back to a graphical environment

---

### Post by mburman23 on 2011-09-22
Thanks for your reply!  I am able to fill the screen with text as you suggested.  The display appears perfect in command line mode.  I was not able to return to the GUI with CTRL-ALT-F8 but I think your test still validates something... exactly what I don't know yet... it appears that the hardware is ok... and that the issue is only in the GUI.  What's next??
 
If it helps... a few additional notes... when the GUI is first launching it attempts to put a splash screen up ( I think it says Ubuntu at the very bottom ) and it does fill the display but it is as if the signal is very out of sync.  The colors have vertical bars running thru it and the text is horizontally shifted 90 degrees... like  |ntu  ubun| (best I can explain). Then the login box appears.  I can only see half of it so I fumble several times to log in but finally do.  And still can only see half of the screen.  The Right side of the display is like an echo or ghost of the right side.  BUT in command line it is all normal and totally usable... Just not in the GUI.
 
Thanks again for helping me!
 
Michael

---

### Post by Hakunka-Matata on 2011-09-22
> **squenson said:**
> First test (FULLY read this message as you won't see it while you run the test! REMEMBER THE STEP 5 ( Ctrl-Alt-F8 ) IN CASE YOU ARE LOST WITH A BLACK SCREEN!):

    1. Press Ctrl-Alt-F4 to get to a terminal mode
    2. Login using your usual user-id and password
    3. Type the command ls several times, just to see if the full screen is working
    4. Logoff with the command Exit
    5. Press [COLOR=Red]Ctrl-Alt-F8[/COLOR] to get back to a graphical environment

Try Ctrl-Alt-F7 instead - it won't fix your problem, but may fix line # 5.

---

### Post by varunendra on 2011-09-22
> **mburman23 said:**
> .... it does fill the display but it is as if the signal is very out of sync.  The colors have vertical bars running thru it and the text is horizontally shifted 90 degrees... like  |ntu  ubun| (best I can explain). Does it work ok in Live session (when you boot from Live Cd and select "Try Ubuntu")?

If you have already installed it, try pressing 'shift' key (perhaps any key) when the computer is booting from the CD. This should bring up advance grub menu. There, select 'Recovery' mode and in the recovery menu, select "FailsafeX" to boot. See if it lets you boot normally. If it does, we may further need to either find a suitable driver, or create a custom xorg.conf file that lets you boot with normal display.

---

