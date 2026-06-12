---
title: "Install unresolved dependencies?"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by three-cushion on 2007-01-17
I aplogize in advance of posting in this thread... but in the PPC thread I got nowhere (except Mark Allan's bit which I did follow with no answers standing out).
Item #1 is a legit Ubuntu install question. Items 2 & 3 are clamav questions. Hope some one here has some ideas on all 3 items.
==========================================================


I have Ver 6.06 LTS installed on my G4 (OS 10.4.8 ). **The G4 Mac system has ClamXav from Mark Allan running quite nicely.**

On Ubuntu I tried once to install clamav, but did not suceed. And, I had updated Universal search in */etc/apt/sources.list*.
In my Latest re-install, I still had 3 unresolved dependicies:
.....  gnome-terminal-data; gnome-terminal; and ubuntu-desktop

When I try to update these (w/ Synaptic), it always fails.

The last (and initial) clamav try ended up with unresolves as well. 3 of the clam files refused to install b/c libclamav1 was unresolved. And, I *think* that was b/c the install still had the ver -2 engine... whereas the -7 engine source is available.

Questions:
1) How are the gnome- & Ubuntu items resolved?
2) Should I re-install clamav (after complete removal first of all Ver -2 files) with
sudo apt install clamav?
3) After a download of the -7 clam engine, how does one install that source? and should it come before or after the clamav installs?

Any help will be greatly appreciated.

Cheers, Jim B
__________________

---

### Post by dcstar on 2007-01-17
> **three-cushion said:**
> 
.......
In my Latest re-install, I still had 3 unresolved dependicies:
.....  gnome-terminal-data; gnome-terminal; and ubuntu-desktop

When I try to update these (w/ Synaptic), it always fails.

.......

How?, what are the messages?

---

### Post by Fitzy_oz on 2007-01-17
> **three-cushion said:**
> I aplogize in advance of posting in this thread... but in the PPC thread I got nowhere (except Mark Allan's bit which I did follow with no answers standing out).
Item #1 is a legit Ubuntu install question. Items 2 & 3 are clamav questions. Hope some one here has some ideas on all 3 items.
==========================================================


I have Ver 6.06 LTS installed on my G4 (OS 10.4.8 ). **The G4 Mac system has ClamXav from Mark Allan running quite nicely.**

On Ubuntu I tried once to install clamav, but did not suceed. And, I had updated Universal search in */etc/apt/sources.list*.
In my Latest re-install, I still had 3 unresolved dependicies:
.....  gnome-terminal-data; gnome-terminal; and ubuntu-desktop

When I try to update these (w/ Synaptic), it always fails.

The last (and initial) clamav try ended up with unresolves as well. 3 of the clam files refused to install b/c libclamav1 was unresolved. And, I *think* that was b/c the install still had the ver -2 engine... whereas the -7 engine source is available.

Questions:
1) How are the gnome- & Ubuntu items resolved?
2) Should I re-install clamav (after complete removal first of all Ver -2 files) with
sudo apt install clamav?
3) After a download of the -7 clam engine, how does one install that source? and should it come before or after the clamav installs?

Any help will be greatly appreciated.

Cheers, Jim B
__________________

You might need to jump to a terminal and run sudo apt-get update

---

### Post by riven0 on 2007-01-18
Yeah, otherwise post the error messages you get here so we can work them out.

---

### Post by three-cushion on 2007-01-18
Thanks for suggestions..

Using sudo apt-get update, successfully updated 7 items...

then got this error message (same if I used Synpatic and Marked 7 items for update...)

SEE Attachment...[ATTACH]23383[/ATTACH]

NOTE: Terminal runs fine; Ubuntu Desktop works OK...  (Maybe no repair is necessary?)

Cheers, Jim b

---

### Post by Fitzy_oz on 2007-01-18
> **three-cushion said:**
> Thanks for suggestions..

Using sudo apt-get update, successfully updated 7 items...

then got this error message (same if I used Synpatic and Marked 7 items for update...)

SEE Attachment...[ATTACH]23383[/ATTACH]

NOTE: Terminal runs fine; Ubuntu Desktop works OK...  (Maybe no repair is necessary?)

Cheers, Jim b

now try sudo apt-get repair in a terminal and it should fix that.  Failing that open synaptic and select the filter broken in the left column, you should find the offending package after which you should be able to remove it or at least no what dependency you need to find to satisfy it.

---

### Post by three-cushion on 2007-01-19
> now try sudo apt-get repair in a terminal and it should fix that. Failing that open synaptic and select the filter broken in the left column, you should find the offending package after which you should be able to remove it or at least no what dependency you need to find to satisfy it.

OK tried the above:
sudo apt-get repair   E: Invalid operation repair

Then on broken:  No broken packages at all 

I did install some add'l packages (backports)   and all installed OK but at the end:

Same  E:     as in the Attachment # 23383 above....hmmmmm?
BUT, I don't think the errors hurt any execution of Ubuntu????
=====================================================
I want to get on to clamav install:

goto root of Home dir
sudo apt-get-install clamav

But I don't believe the engine that drives clamav will be installed this way....

If it doesn't, then, since I have the latest engine source on Desktop:
open the source dir and enter:

./configure --prefix=/usr/local/clamav
make
sudo make install 

Where have I missed a step (if any)....

Cheers, Jim B:confused:
I know so little I feel I'm dangerous here....:frown:

---

