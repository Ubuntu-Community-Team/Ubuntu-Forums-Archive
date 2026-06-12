---
title: "Incorrect Password"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by geo14618 on 2007-01-15
I installed ubuntu 6.10 Alternative on My IBM 780XD Laptop. When I enter the oem Login and then Password it says incorrect login. I really have to type fast or the Password Screen goes blank and thats the way it stays. I installed it 2 times, and get the same results. The installation goes fine. It won't accept the Password I setup on installation.

---

### Post by taurus on 2007-01-15
You won't see the echo on the screen when you type your password.  That's normal.  Just type your complete password and hit the return.

---

### Post by geo14618 on 2007-01-15
OK but why won't it accept my password as correct.

---

### Post by taurus on 2007-01-15
Are you sure you type in the correct password?  Again, it looks like the cursor doesn't move when you type in your password so just type it in and hit the return key.

---

### Post by geo14618 on 2007-01-15
I am Possitive I Entered the correct password.

---

### Post by taurus on 2007-01-15
Remember, lower case letters are not the same as upper case letters since Linux/Unix is case sensitive.

---

### Post by geo14618 on 2007-01-15
I never use caps so i entered the correct password. It still says ( incorrect login)

---

### Post by taurus on 2007-01-15
Duplicate...

---

### Post by taurus on 2007-01-15
So you use **oem** as the login name and the same password that you've created during the installing process, right!  I assume you used the alternate CD and picked the oem version.
 
p.s.  With Edgy alternate CD, you don't have to pick the oem option (second option on the menu).  Why not pick the first option to install it as you would normal do...

---

### Post by geo14618 on 2007-01-15
Correct on every count

---

### Post by geo14618 on 2007-01-15
OK Ill try that tomorrow and see if it works. Thank You

---

### Post by verynice2cu on 2007-01-21
I encounter exactly the same problem. However, I do not remember which version I downloaded. I know it's 6.10 Final. OEM dowsn't ring a bell. However, I too installed it twice with the same result. I cannot login with the name and pass combination. And I know they are correct. I write them down!
Correction: I did also use the alternate iso-version!

---

### Post by taurus on 2007-01-21
> **verynice2cu said:**
> I encounter exactly the same problem. However, I do not remember which version I downloaded. I know it's 6.10 Final. OEM dowsn't ring a bell. However, I too installed it twice with the same result. I cannot login with the name and pass combination. And I know they are correct. I write them down!
Correction: I did also use the alternate iso-version!

Boot into recovery mode from GRUB menu and at the prompt, post the output of this command here.

```
ls -la /home
```

---

### Post by verynice2cu on 2007-01-21
Thanx Taurus. I'll try to figure this out. It may take a while.

---

### Post by verynice2cu on 2007-01-21
Taurus,
What happened is that it showed me that the username was typed two times in a row. Let's say my username had been entered by me as 'apple', it showed up as 'appleapple'. I have rebooted and used this double username to login. Guess what? This double username was accepted and I was able to login! I am very sure I did not during set up enter this username twice. Very interesting. 
Thank you very much so far, Taurus. I am actually using Ubuntu now, which is virgin territory to me. I am sure I now will encounter other problems, but I really appreciate your help. Any idea how this problem may have occurred?

---

### Post by taurus on 2007-01-21
> **verynice2cu said:**
> Taurus,
What happened is that it showed me that the username was typed two times in a row. Let's say my username had been entered by me as 'apple', it showed up as 'appleapple'. I have rebooted and used this double username to login. Guess what? This double username was accepted and I was able to login! I am very sure I did not during set up enter this username twice. Very interesting. 
Thank you very much so far, Taurus. I am actually using Ubuntu now, which is virgin territory to me. I am sure I now will encounter other problems, but I really appreciate your help. Any idea how this problem may have occurred?

Not sure why but you can change it back to "apple" if you wish or are you happy with appleapple (two a day is good for you) as your username?

---

### Post by verynice2cu on 2007-01-21
It doesn't really matter what username I use as long as it  works. I have installed Ubuntu to get to know Linux. Open source software is growing rapidly and you have to start using it some day. The next problem however has already presented itself. My screen is monochrome: blueish with black lettering - very low contrast. Before starting a new thread I will try to solve this problem myself first. Thanks again Taurus.

---

### Post by taurus on 2007-01-21
Good luck with the screen/resolution.  And if you decide to start a new thread, don't forget to include the spec of your machine especially the graphic card and the monitor.

---

### Post by verynice2cu on 2007-01-21
I will. Ciao.

---

