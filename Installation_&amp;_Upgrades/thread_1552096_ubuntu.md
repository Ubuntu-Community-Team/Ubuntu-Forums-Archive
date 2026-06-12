---
title: "ubuntu"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by wavemaker on 2010-08-13
Why is ubuntu using the left side  to put the open/close/minimize etc?

---

### Post by Segofam on 2010-08-13
This is not the answer but...
I had the same issue, and found the answer in these forums...ages ago...do a search and will find the answer. I changed them to the right side.

---

### Post by go2dell on 2010-08-13
There was a HUGE discussion about this when the decision was made.  Here's a post to get you started: [Why Window Button Placement Doesn't Matter (at WorksWithU)]("http://http://www.workswithu.com/2010/03/16/why-window-button-placement-doesnt-matter/").

You can switch the buttons to be more Kubuntu-like, if you wish.  Or just keep using Kubuntu.  :D

---

### Post by TNT1 on 2010-08-13
Use Ubuntu Tweak... put the buttons anywhere you like...

---

### Post by Joe of loath on 2010-08-13
The developers (Or canonical, I forget) were planning on putting something on the right hand side, so moved the buttons to the left. To be honest it takes so little time to adjust it doesn't matter, and I rarely find myself going to the other side of the window on different OSs and GUIs.

---

### Post by Sef on 2010-08-13
> The developers (Or canonical, I forget) were planning on putting something on the right hand side, so moved the buttons to the left. 

Are planning - there are [some plans]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633/comments/564") for the right side.

---

### Post by Segofam on 2010-08-13
> **Segofam said:**
> This is not the answer but...
I had the same issue, and found the answer in these forums...ages ago...do a search and will find the answer. I changed them to the right side.

I just found what I did to change it...

gconftool -s /apps/metacity/general/button_layout -t string menu:minimize,maximize,close

For those that are afraid of the terminal and their copy-paste functionality, you can follow these steps:
Press ALT-F2 to open the application launcher.
Enter &#145;gconf-editor&#146;
Navigate to Apps > Metacity > General > Button Layout
Change the string value to &#145;menu:minimize,maximize,close&#146;
Exit gconf-editor

Kind regards.

---

### Post by wavemaker on 2010-08-14
Gooday all and thank you for that. I did the "Press ALT-F2 to open the application launcher.
Enter &#8216;gconf-editor&#8217;
Navigate to Apps > Metacity > General > Button Layout
Change the string value to &#8216;[COLOR="Red"]menu:minimize,maximize,clos[/COLOR]e&#8217;
Exit gconf-edito"
But that is what it's already got there.
Sorry, didn't even see it happen. Problem solved. Thank you!

---

