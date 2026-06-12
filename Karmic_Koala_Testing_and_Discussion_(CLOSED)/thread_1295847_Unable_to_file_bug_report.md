---
title: "Unable to file bug report"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mike Easter on 2009-10-20
Can someone help me file a bug report?

If I go to launchpad and click to file a bug report, I am flipped back to the help page which tells me how to file a bug report.

That doesn't get it done.

This problem requires that I file the bug report at launchpad, not from some application's menu or from ubuntu-bug.

This is about a regression from 9.04 which booted properly.  Now 9.10 with command adjustment for vga=795 boots with an invisible cursor caused by an nvidia problem.

This regression needs to be fixed before 9.10 is released, IMO

---

### Post by 23meg on 2009-10-20
[QUOTE=Mike Easter]If I go to launchpad and click to file a bug report, I am flipped back to the help page which tells me how to file a bug report.[/QUOTE]

On that page there's an alternative link you can use to file a bug report directly at Launchpad.

---

### Post by Mike Easter on 2009-10-20
The ubuntu help page for reporting bugs...

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

 ....describes in considerable detail how to file a report and one - the third one - of those ways is to go to launchpad which is at... 

[https://launchpad.net/distros/ubuntu/](https://launchpad.net/distros/ubuntu/) 

On that page in the right column, there is a Get Involved link for... 

Get Involved
    * Report a bug  

... which Report a bug is a link

[https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)

... which link redirects to 

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by 23meg on 2009-10-20
Does [https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect) not work for you?

---

### Post by philinux on 2009-10-20
Also, once you've filed the bug using the no redirect link then run this in a terminal.

```
apport-collect bugnumber
```

---

### Post by Mike Easter on 2009-10-20
> **23meg said:**
> Does [https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect) not work for you?

That works.  Thanks, I didn't know about the no-redirect trick.

Since starting this thread, I've also 'advanced' in my ability to submit a bug report from the failed bootup in karmic, which is what this is about, but I can't complete the report.

default boot karmic gives bad graphics;  default boot + vga=795 in the commandline gives a graphical desktop with an invisible mouse cursor

alt-F2 allows me to ubuntu-bug, but that progresses to a browser to complete the report and I can't navigate with the keyboard to get into the section where I need to edit a summary, so that report fails

---

