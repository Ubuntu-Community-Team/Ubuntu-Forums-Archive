---
title: "install with acpi=off...how do I do it?"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by Kevin Jones on 2008-10-16
Hello all
I have an old HP pavillion desktop. I get a message just after booting that the system tables cannot be read.
A 02811201 ACPI: unable to load system description tables.
I have found out that I need to install the system with ACPI=off.
My problem is that I do not know enough about the manual installation to set the acpi=off and then ask the device to install. I can access a shell from the live cd, but, again, do not know what commands to give the shell.

Can anyone who has installed on an old pc and knows how to switch off the ACPI and then install help me?

Thansk for the help

Kevin Jones

---

### Post by Ayuthia on 2008-10-16
acpi=off is a boot parameter.  Are you getting this when you are using the live CD?  If so, you should be able to add this command when you start up the live CD.  When the option screen comes up, it should allow you to update the commands by pressing F6 (If I remember correctly).  From there, a line should come up at the bottom of the screen and at the end of the line, you just need to add acpi=off and then press enter.

Hope that helps.

---

### Post by Kevin Jones on 2008-10-17
Ayuthia,

Thanks, just afer I set the language option I can indeed press F6  which allows me to install with ACPI=off.
As it happens this solution was to the problem of not being able to read the system description tables. I did install Intrepid with this option and it seemed to go well. I am able to login in to gnome but as soon as I do it freezes to blank grey screen.
Thanks for the advice, it was accurate. I am still unsure how to get around the system tables problem as this solution does not seem to have worked.
As a point of interest..opensuse 11.0 (which I don't really like as an operating system) installs without a hitch. I really would like to install Ubuntu
I will be googling this weekend for another solution
Thanks for the help. 


Kevin Jones

---

