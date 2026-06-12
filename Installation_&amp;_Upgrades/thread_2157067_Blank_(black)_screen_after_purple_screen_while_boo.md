---
title: "Blank (black) screen after purple screen while booting"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by ThePsych0naut on 2013-06-24
I know there have been many threads regarding this but I cant get them to work, plus I feel the need to explain my situation more clearly. Here are the steps of what I do and where I get stuck:
1. I start my laptop (hp pavilion 1003tx, core i5, Windows7 32 bit, 2 gb ram) and it shows the screen where I can choose Windows 7 or Ubuntu. There is also Windows Diagnostic Tools (no safe mode for ubuntu in this menu like it does in 13.xx, mine is 12.04.
2. Once I choose Ubuntu, there is a black screen with 3 lines, it goes away fast but I do read a word Error, though cant read the complete thing because it goes away pretty fast. (This used to happen before also and Ubuntu started up just fine so I am guessing this is not where the problem is) Note: I will try and get every word from the screen if you insist you need to know what the error is, so let me know if u want that)
3. After this I get a purple screen which stays for about 5-8 seconds.
4. Following this I get just a blank/black screen which stays there forever OR the Ubuntu loading screen (the one with dots below the Ubuntu text) which stays there for few microseconds and then goes back to black screen and gets stuck there. Note that I CANNOT access the terminal or anything from here and there is NO cursor like some people eperience.
5. After waiting for quite sometime (5-10 minutes) I press the power button. DOING THIS brings back the ubuntu loading screen that I described earlier but in a second or two the laptop powers down. Note that this screen only shows up when I press the power button so this is obviously not the solution, since it powers down after a second.

I tried increasing the delay of the lightdm as mentioned in this thread ([http://www.webupd8.org/2013/01/ubuntu-lightdm-black-screen-when-using.html](http://www.webupd8.org/2013/01/ubuntu-lightdm-black-screen-when-using.html)) and tried GDM method as well but i cannot get the lightdm menu to open. The error shown is gtk error : cannot open menu (or something of that sort). This is seems a bit lame since the guy whos has shown screen shot of the menu in the tutorial is running it after booting the OS. How the **** can I do that if I cannot get my OS to boot. While writing this thread I came across a solution related to the acpi so Im gonna try that while I wait for replies on this one. 

P.S. : If any more details (regarding errors or pc) are required, then let me know and I will post more info.

---

### Post by gordintoronto on 2013-06-24
Have you reviewed this: [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

What is the video adapter in your computer?

If you have a video camera, or a phone which shoots video, you might be able to capture the error message -- which is no guarantee that it will lead to an answer. However, it might give you something to plug into Google.

The fact that you are not offered a Ubuntu recovery mode is a cause for concern. How much disk space did you give Ubuntu?

---

### Post by MidnightGrey on 2013-06-26
> 5. After waiting for quite sometime (5-10 minutes) I press the power  button. DOING THIS brings back the ubuntu loading screen that I  described earlier but in a second or two the laptop powers down. Note  that this screen only shows up when I press the power button so this is  obviously not the solution, since it powers down after a second.
when ubuntu shuts down, it displays the loading screen (as a shutdown screen). So good news is your OS is working, just the display isn't. (which is an eaiser fix i suppose).

---

### Post by coldraven on 2013-06-26
I'm not quite sure because it is a long time since I messed with Grub but if you press the shift key while booting do you get more options?

---

### Post by markbl on 2013-06-26
In step 4 you say you "CANNOT access the terminal" - do you mean that ctrl+alt+f1 does not bring up a terminal session?

---

