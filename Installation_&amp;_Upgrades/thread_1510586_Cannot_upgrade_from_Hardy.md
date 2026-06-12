---
title: "Cannot upgrade from Hardy"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by hambidextrous on 2010-06-15
I am using a dell mini with Hardy and do not seem to be able to upgrade at all.  I have tried following the instructions in the ubuntu documentation but the upgrade manager finds no new releases to upgrade to.  Does anyone have any suggestions on what my be preventing me from upgrading?  My goal is to get to 10.04.

---

### Post by cariboo on 2010-06-16
Make sure Hardy is fully up-to-date first, that may be what's holding you back. I intend on installing Hardy, then updating to Lucid, but that won't be for a couple of days.

---

### Post by hambidextrous on 2010-06-19
The update manager shows that I am up to date, but no option to upgrade ever.  I don't know if there is something I have installed that would be preventing this, is their a way to check?

---

### Post by kansasnoob on 2010-06-19
Please post the output of:

```
cat /etc/issue
```

and:

```
uname -a
```

Also go to System > Administration > Software Sources and click on the Updates tab. Towards the bottom be sure the selection "show new distro upgrades" option is set to "LTS only".

---

### Post by hambidextrous on 2010-06-19
Below is the output for: cat /etc/issue

```
Ubuntu 8.04.2 \n \l
```

Below for: uname -a

```
Linux hambidextrous 2.6.24-27-lpia #1 SMP Wed Feb 17 22:14:54 UTC 2010 i686 GNU/Linux
```

As for the "show new distro upgrades" option, it is not visible in the Software Sources, Updates tab.  In the Updates tab the only options I have are the following:
[INDENT]
**Automatic updates**
(check box, which is checked) Check for updates: (scroll field with the options: Daily(currently selected), Every 2 days, Weekly, and Every 2 weeks)
Below that are two radio circle options:
(first option, not selected) Download all updates in the background
(second option, selected) Only notify about available updates[/INDENT]

---

### Post by kansasnoob on 2010-06-20
> **hambidextrous said:**
> Below is the output for: cat /etc/issue

```
Ubuntu 8.04.2 \n \l
```

Below for: uname -a

```
Linux hambidextrous 2.6.24-27-lpia #1 SMP Wed Feb 17 22:14:54 UTC 2010 i686 GNU/Linux
```

As for the "show new distro upgrades" option, it is not visible in the Software Sources, Updates tab.  In the Updates tab the only options I have are the following:
[INDENT]
**Automatic updates**
(check box, which is checked) Check for updates: (scroll field with the options: Daily(currently selected), Every 2 days, Weekly, and Every 2 weeks)
Below that are two radio circle options:
(first option, not selected) Download all updates in the background
(second option, selected) Only notify about available updates[/INDENT]

Hmmm, Hardy should be up to 8.04.4 w/kernel 2.6.24-28 AFAIK. So I wonder if Dell used a spin-off of UNR?

Have you  tried checking any of the Dell documentation?

---

### Post by hambidextrous on 2010-06-20
I have not yet, but I will look and post what I find.  **See Below.**

Do you know of any ways for me to get up to the current version?  Or anything else (other than Dell) that may show why its not at 8.04.4?

**Update:** It does look like Dell installed a OS based on 8.04, someone said it was modified to limit the RAM seen/used.  I also read that they used the lpia because it works well with the Atom processor.  It sounds like the custom version was standard before 9.04.  I am looking to see what else I can find.  Thanks for pointing me in the right directions.

---

### Post by hambidextrous on 2010-06-20
So, it sounds like I need to completely remove the 8.04.2 version I have and install the normal version (or a later ubuntu version).  I don't really have a clue how I would go about doing this.  Can someone point me to some documentation that will outline how to remove my current OS and install a new one (or explain it if it is fairly simple)?

---

### Post by kansasnoob on 2010-06-20
Well I'm thinking with a mini you have no CD drive, eh?

If so you'd be limited to using a Live USB and I can't stress the importance of trying the Live version first strongly enough!

Every release has bugs and such:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)

You may also want to consider UNR:

[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

To be honest I'm just not sure.

---

### Post by hambidextrous on 2010-06-20
I would prefer to use UNR.  I have been looking at Lucid (as far as I can tell it is possible to install it), but need to get a USB, and then figure out how to boot from the USB to test, then figure out how to remove my current version and install the new.

I guess I have some work to do, luckily I'm not in a rush.  Thanks for the help.

---

### Post by nemoursr on 2010-07-11
> **kansasnoob said:**
> Well I'm thinking with a mini you have no CD drive, eh?
If so you'd be limited to using a Live USB and I can't stress the importance of trying the Live version first strongly enough!
Every release has bugs and such:
[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes)
You may also want to consider UNR:
[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)I'm in the same situation as hambidextrous, but am an inexperienced user.  I do have an external cd drive.  When you say "try the Live version first," does that mean I can download Lucid to my cd and then try it out before getting rid of 8.04?  If that's the case, how do I tell my computer (Dell mini 10) to boot from the cd?  What does UNR mean?

Thanks.

---

