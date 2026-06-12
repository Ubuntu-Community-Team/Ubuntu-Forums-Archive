---
title: "ubiquity-qt crashes"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by qra0 on 2010-02-25
If you want people to install Alpha 3 and provide feedback & bug reports, then please provide a working installer. 

D'oh ](*,)

---

### Post by Yeeha on 2010-02-25
I think what he means is blank screen with live cd. I remember older ubuntu versions had safe graphics option or something like that what to use if default way didnt work. As i got blank screen i had to use that option to use live cd but it seems this option was considered not necessary :S and removed. So when i tryed to install kubuntu today i couldnt. There was in help that write vga=771 if you have trouble with laptop but that didnt work or i didnt know where/how to write it on that bootline.

---

### Post by qra0 on 2010-02-25
> **Yeeha said:**
> I think what he means is blank screen with live cd. I remember older ubuntu versions had safe graphics option or something like that what to use if default way didnt work. As i got blank screen i had to use that option to use live cd but it seems this option was considered not necessary :S and removed. So when i tryed to install kubuntu today i couldnt. There was in help that write vga=771 if you have trouble with laptop but that didnt work or i didnt know where/how to write it on that bootline.

No I mean ubiquity_qt just dies back to the desktop when you click the forward button with no error messages even when launched from Terminal.

---

### Post by VMC on 2010-02-25
> **qra0 said:**
> No I mean ubiquity_qt just dies back to the desktop when you click the forward button with no error messages even when launched from Terminal.

What was the message inside that terminal? Also look at "/vat/log/syslog" filter for ubiquity messages. Maybe file a bug report.

---

### Post by qra0 on 2010-02-25
> **VMC said:**
> What was the message inside that terminal? Also look at "/vat/log/syslog" filter for ubiquity messages. Maybe file a bug report.

That's the problem, there are no error messages.

---

### Post by 23meg on 2010-02-25
This is not a bug tracker, or a channel for communication with developers. Please file a bug report; try running it with ```
ubiquity --debug
``` and search /var/log/syslog for Ubiquity related output.

---

### Post by qra0 on 2010-02-25
> **23meg said:**
> This is not a bug tracker, or a channel for communication with developers. Please file a bug report; try running it with ```
ubiquity --debug
``` and search /var/log/syslog for Ubiquity related output.

Like I said, there are NO error messages. There is nothing.

And please don't change any more of my thread titles :)

---

### Post by 23meg on 2010-02-25
> **qra0 said:**
> Like I said, there are NO error messages. There is nothing.

You didn't say that for "ubiquity --debug", though.

[QUOTE=qra0]And please don't change any more of my thread titles :)[/QUOTE]

It would help if you titled your threads to reflect the subject you need help with.

---

### Post by qra0 on 2010-02-25
> **23meg said:**
> You didn't say that for "ubiquity --debug", though.

There are NO messages. Nada, nothing, zero.

> **23meg said:**
> It would help if you titled your threads to reflect the subject you need help with.

I wasn't asking for help...

---

### Post by 23meg on 2010-02-25
> **qra0 said:**
> 
I wasn't asking for help...

Then you're at the wrong place, since the purpose of this forum is to help people debug and report defects, not communicating with developers.

If you need further help with different issues, please start an appropriately titled thread with a summary of your progress.

---

