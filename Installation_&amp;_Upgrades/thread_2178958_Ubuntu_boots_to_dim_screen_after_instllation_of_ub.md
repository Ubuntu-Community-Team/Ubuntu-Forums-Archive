---
title: "Ubuntu boots to dim screen after instllation of ubuntu 12.04. Backligh stopped workin"
date: 2013-10-05
forum: Installation &amp; Upgrades
---

### Post by pQNmyG4 on 2013-10-05
Dear all,

I have just installed the latest long supported release ubuntu 12.04 on Dell xps 13 L322X.
After which ubuntu started to boot to dim screen. almost impossible to see anything on the screen. 
The current kernel version is 3.8.0-31-generic.
Interestingly, when I boot with earlier kernel version 3.8.0-29-generic everything is fine.
Does any one know how to make it work for the new kernel 31-generic?

P.S. my laptop has also windows 8 installed and UEFI.

---

### Post by ping-wu on 2013-10-06
Open a terminal and enter the following commands:

sudo su

(enter password)

echo 300 > /sys/class/backlight/acpi_video0/brightness

if it changes the backlight brightness, then post your positive result.  We will make the command persistent.

---

### Post by pQNmyG4 on 2013-10-06
it's strange, I cannot write to that file even as a super (root) user. I got the error "bash: echo: write error: Invalid argument" .
I have also tried to modify that file using vi and gedit, they both refuse to write to the file and give only error messages.

---

### Post by varunendra on 2013-10-06
> **pQNmyG4 said:**
> it's strange, I cannot write to that file even as a super (root) user. I got the error "bash: echo: write error: Invalid argument" .
I have also tried to modify that file using vi and gedit, they both refuse to write to the file and give only error messages.

Because that value is not suitable for all cards. Different cards accept different values. To get an idea of which ones may be acceptable to yours, please post the output of -
```
for i in `ls /sys/class/backlight/`; do echo -e "\n $i"; cat /sys/class/backlight/$i/{brightness,max_brightness,actual_brightness}; done
```

**EDIT:**
Added echo -e "\n $i" to make it more useful.

---

### Post by ping-wu on 2013-10-06
do the following instructions:

cd /sys/class/backlight

ls

and see how many sub-folders you have there.

---

### Post by varunendra on 2013-10-06
> **ping-wu said:**
> do the following instructions:

cd /sys/class/backlight

ls

and see how many sub-folders you have there.

That, and cat command for relevant files in each sub-folder is already included in the script I posted. :)

The "for **[COLOR="#FF0000"]i[/COLOR]** in `ls /sys/class/backlight`" part covers all the directories (sub-folders) and processes them one-by-one through variable "**[COLOR="#FF0000"]i[/COLOR]**".

The rest of the command reads the values of "brightness, max_brightness, and actual_brightness" files in each of these directories and returns their values. Try it, and you'll get the idea.

Based on these values we can guess acceptable values for the brightness file.

It is just a "read everything in one-go" recipe ;).

---

