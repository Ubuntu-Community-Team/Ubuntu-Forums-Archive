---
title: "error messages"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by gary-aus on 2011-05-23
I have just recently updated my HP MINI 110 1000 Netbook.  It had a HP version of linux on it which is Demian/Ubuntu based.  I took took it off because HP seemed to be no longer doing updates.  
I made a USB stick of Ubuntu remix for a netbook version 10.10,  I used the USB stick to load and install the OS on to the netbook.

Every thing seems to work fine but I get a heap of error messages each time I boot.  It all happens so fast that it has been difficult to read enough to even know what the message is.

The message reads 

udevd[80] : worker 171 did not accept message -1 connection refused - kill it

The same messages is repeated many times except that the number 171 is incremented by 1 each time.

I have also notices at some times the opening word of the error messages seems to be uvded and then it changes to udevd,

Has anyone any idea as to what the messages relate to and if so how to fix it?

thanks

---

### Post by dargaud on 2011-05-23
Type 'dmesg' in a terminal, you should find the same error messages.

---

### Post by gary-aus on 2011-05-23
I have looked at the dmesg file and can not see the error messages there persay.  I have attached a txt file of the dmesg file in the hop it may throw some light on the issue
the file is dmesg-hp.txt

Thanks

---

### Post by MAFoElffen on 2011-05-23
> **gary-aus said:**
> I have looked at the dmesg file and can not see the error messages there persay.  I have attached a txt file of the dmesg file in the hop it may throw some light on the issue
the file is dmesg-hp.txt

Thanks
I didn't see an attached file (dmesg-hp.txt).  

You know-- If you toggle over to one of the text console sessions using <cntrl><alt><F!>.... Those messages will still be there.  You can use the linux hotkeys <Shift><Page Up> and <Shift><Page Down> to review what was on the screen a page at a time. (Up or Down, depending which hotkey you use.)  

This lets you review what is there in the buffer, until it gets full and pushes the previous out <> or the screen gets cleared and flushes it out of the buffer.

---

### Post by gary-aus on 2011-05-27
Sorry I did not get back earlier, had great family news which took preference over computers.

I used the <ctrl><alt><F1> combination and did get some information.   No matter what I did I could not get the page up and down to work so I only got some of the information re the problem at start up.

udevd[80] : worker {93) did not accept message -1 (connection refused), - kill it

this was repeated many times increasing the worker number.   As I indicated I did not get it all but that which came up on the screen had the following numbers;

119
120
122
124
182
183
198
199
200
212
213
217

217 was the last number before the log on command line was present.
The number 93 was the first I managed to catch visually.  there were number between 93 and 119

I think the file I thought I attached was too large.  I have since found that the forum accepts 18kB files as attachments and the dmesg file was 22kb.   I will see what I can cut out to reduce the size without loosing too much.

Thanks for the assistance

---

### Post by gary-aus on 2011-05-29
Just to advise the error messages at start up have been fixed.   I did an update to 11.04 and the error messages are no longer there.

I do appreciate you time and advice.  I have learnt a number of things from your replies.  Again thanks

---

### Post by oldgeekster on 2011-06-17
> **gary-aus said:**
> Just to advise the error messages at start up have been fixed.   I did an update to 11.04 and the error messages are no longer there.

I do appreciate you time and advice.  I have learnt a number of things from your replies.  Again thanksI didn't see them for a while after updating my notebook to 11.04 - but now they are back with a vengeance. :(

Something changed, probably in an update.  A check on the bug list still shows the priority as low and unassigned.  I agree with the low part, its just kind of irritating to have it slowing the otherwise wonderfully improved boot time for the last two versions of Ubuntu.

---

