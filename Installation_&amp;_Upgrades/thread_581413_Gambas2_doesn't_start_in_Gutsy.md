---
title: "Gambas2 doesn't start in Gutsy"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by hansson_14 on 2007-10-19
Hi,

Originally I had both Gambas 1 and 1.9.49 installed parallell.

1. I upgraded from Ubuntu 7.04 to Ubuntu 7.10 using built-in upgrade.
Everything (else) works fine now.
2. I uninstalled Gambas using Ubuntu's Add/remove tool.
3. I installed Gambas2 using Ubuntu's Add/Remove.

Now, Gambas2 refuses to start.
a) No message clicking the icon in the program list.
b) Message trying to start from terminal:

ERROR: #27: Cannot load component 'gb.form.dialog': cannot find library file

At Gambas forum another user reports the same situation.

Gambas forum says:
"It's quite obvious that Ubuntu packages are broken after your upgrade and
gambas2-gb-form package doesn't exist or just doesn't work. You should pass this information to Ubuntu bug tracking system and wait for them to fix it. You can also use Debian instead ;-) "

So, something's missing... or?
What should I do?

Regards,
Fredrik Hansson

---

### Post by hansson_14 on 2007-10-19
I tried to install the latest Gambas from
[http://gambasrad.org/documentation/current-developer-snapshot](http://gambasrad.org/documentation/current-developer-snapshot)

Still the same problem - Gambas didn't start.

Then I completely removed all gambas-stuff using Synaptic and I installed the latest development version again (as above).
Now everything's fine!

So, there could be some fault in Ubuntu's Gambas package.

/Fredrik

---

### Post by JohnEv on 2007-10-22
Hi,
    I have done a clean install of Gutsy and installed Gambas.  It runs but there appear to be several missing bits.  The serial port example loads but when trying to open the form I get the message: "Cannot open file  -- component missing  - FForm.CreateControl.833.
  I had no problems running this in Fiesty.
Regards
JohnEv

---

### Post by JohnEv on 2007-10-23
Re missing bits
  Today I removed Gambas using Add/Remove, then installed again using Administration/Synaptic Package Manager.  Now appears to be fully working
Regards
JohnEv

---

