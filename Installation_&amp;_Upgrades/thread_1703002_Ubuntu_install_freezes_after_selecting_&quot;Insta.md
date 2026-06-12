---
title: "Ubuntu install freezes after selecting &quot;Install Ubuntu&quot;"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by sviva on 2011-03-08
After selecting "Install Ubuntu", the screen goes blank and nothing happens.  I am using a HP laptop and am trying to install Ubuntu 9.10 from a CD I ordered from ubuntu.com.
:confused::confused::confused:

Thanks for any help!

---

### Post by mörgæs on 2011-03-08
Installing 9.10 is a waste of time, since it will only be supported for a month more. 

Best is to burn 10.04 and/or 10.10 from the ISO found at 
[http://www.releases.ubuntu.com](http://www.releases.ubuntu.com)
and install the one that works best on your system.

---

### Post by Rubi1200 on 2011-03-09
I agree with mörgæs that installing 9.10 is probably not a good idea since support runs out in April.

That said, your description of the problem sounds like a graphics issue.

What graphics card do you have installed?

Also, how much RAM is there and what other operating systems are on the laptop?

Thanks.

---

### Post by sviva on 2011-03-12
Thank you for your reply, and sorry for getting back to you late.
When trying to install Ubuntu 10.10, the screen is kinda a purple color, and it has what looks like a calender, = a person with a circle around him.  That is there for a few seconds.  After that the screen goes black, and there are many lines of numbers and letters.  The first line looks like this: [   0.000000] Call Trace:
and the last line is 
[    0.000000] [<c08190d7>] i386_start_kernel +0xd7/0xdf
I have at least 1G of ram and am using the integrated graphics in my HP pavilion ze4900

Thank you in advance for any further help.

---

### Post by mörgæs on 2011-03-12
It sounds like you need to add boot options:

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://www.ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

The symbol you saw is 'keyboard-man' meaning 'push any key to get to the boot menu'. You will need that when applying the boot options.

---

### Post by sviva on 2011-03-13
Thank you for your quick reply,
I pressed a key at the keyboard - man screen, and got to boot options.  I tried the install with each one enabled separately (I enabled one and then hit "Install Ubuntu") but each time I did that I got the same result I mentioned in my last post.  After that, when I tried enabling all of them at once, the screen turned blue (that never happened before), the CD spun down, and nothing happened.

Thank you for any further help.

---

### Post by mörgæs on 2011-03-13
Is this the result of both 10.04 and 10.10?

---

### Post by sviva on 2011-03-14
> **mörgæs said:**
> Is this the result of both 10.04 and 10.10?

No this Is the result of 10.10.  I will try 10.04 and post what happens.

Thanks for your help.

---

### Post by sviva on 2011-03-19
Thank you for your replay,
On 10.04, I again tried all the boot options separately, and on boot options noapic, nolapic, and edd=on, I got something similer to
[ 0.000000] [<c08190d7>] i386_start_kernel +0xd7/0xdf
again.  On all the other options I got just a blank screen.

Thank you for any further help.

---

### Post by sviva on 2011-03-24
> **sviva said:**
> Thank you for your replay,
On 10.04, I again tried all the boot options separately, and on boot options noapic, nolapic, and edd=on, I got something similer to
[ 0.000000] [<c08190d7>] i386_start_kernel +0xd7/0xdf
again.  On all the other options I got just a blank screen.

Thank you for any further help.
Please help!

---

### Post by mörgæs on 2011-03-24
Please give a full description of your hardware. 

Have you tried testing the memory of the machine?

---

