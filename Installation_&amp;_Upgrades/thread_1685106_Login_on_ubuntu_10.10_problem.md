---
title: "Login on ubuntu 10.10 problem"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by fgking on 2011-02-10
I spend a huge amount of time to get ubuntu 10.10 installed after many crashes with error 5. I have burnt many CDs and downloaded many images. Finally I took the advice of someone in one of the forums who suggested that if you have dual memory chips in the pc, remove one and install. I have tried that with alternative CD using vga=771 at prompt. At last the installation was completed without a crash. To my surprise when I rebooted and tried to login my password was declined. I am absolutly sure it was the correct password. I was even more surprised when I was able to login on the terminal both as a user and supervisor but not on the desktop login. Could somebody please help me how to get to the desktop with menus etc. I am new to all this. Many thanks

---

### Post by P4man on 2011-02-10
both username and password are CaSE SEnSitiVE. Make sure you dont make a mistake in the capitalization, check that shift lock isnt on etc. Also, and especially if you have a non qwerty keyboard, perhaps your didnt configure it properly. In the login screen, click your name, then check at the bottom that the correct keyboard layout is selected. 

Also, rather than clicking your name, try clicking "other" and see if you can type the password in the username box, just to verify the keyboard is working properly.

If none of that helps, its not hard to change your password. Reboot and select the ubuntu recovery option in grub menu (if you dont see gub menu, hold down the shift key after the bios splash). Select the root terminal. 

Then type in:

```
passwd yourusername
```

BTW, Im not sure what you mean by being able to log in to a terminal as both regular user and superuser? You shouldnt be able to login as root, as the account ought to be disabled with an unknown password. You use "sudo" to elevate your own user account to root, but you still log in with your normal user.

---

### Post by fgking on 2011-02-10
Thanks, yes I was able to login using the text terminal and typing sudo su then my username and password, no problems at all. So if the terminal accepts my password, it just does not make sense that I am not able to login on the desktop. I am familiar with lowercase situation. I have had this problem even when I wanted to try ubuntu on CD. I just don't understand it.

---

### Post by P4man on 2011-02-10
Like I said, verify your keyboard layout in gdm at the bottom and by clicking "other", and type your password there so you can see what appears on screen. You can even click the "universal access" icon to enable an onscreen keyboard and use that to enter your password. I think its just a matter of wrong keyboard layout.

---

### Post by fgking on 2011-02-10
I did all what you said, it did not work. I have entered the password on the usename to be able to read the output, it was correct. I changed my password at the root prompt and I tried to login with new password, no luck. there must be another solution.

---

### Post by grahammechanical on 2011-02-10
When we install we select a language and a keyboard layout. Could there be a mismatch between the language and the keyboard layout. When all else fails - think of something stupid. That is my motto.

Regards.

---

### Post by P4man on 2011-02-10
> **fgking said:**
> I did all what you said, it did not work. I have entered the password on the usename to be able to read the output, it was correct. I changed my password at the root prompt and I tried to login with new password, no luck. there must be another solution.

Are you sure its actually rejecting the password, perhaps its logging you in and back out instantly instead. Try typing a WRONG password, you should hear a short low beeping MUP sound. Is it different when you enter the correct password?

Also try creating a new user from the command line:

```
sudo useradd -d /home/testuser -m testuser
```

Set a password for him:

```
sudo passwd testuser
```

Then try loggin in as testuser.

---

### Post by fgking on 2011-02-11
I think I know why this is happening. I can login on safe mode Gnome but not on the normal desktop. It is because I don't have enough memory. I thought 512 mb was enough according to the requirements I read about. I have installed XORG to minimise the memory used but it did not make any difference. I have unlocked the login system and allowed myself access in safe mode and automatic access without password. Is safe mode access good enough to use?

---

