---
title: "I need help making a custom kernel to fix Smartboard on 10.04"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by bbehrendt on 2010-05-21
I am a little disappointed that this is the solution Smart gave me to make their product work in Ubuntu 10.04.    The problem is that the mouse will jump to the top left when a smartboard is plugged in.  There was a simple fix for 9.10 and below but in 10.04 that fix no longer works.

My first attempt at compiling custom has failed (not even sure where).  So I am asking this community for help.  Below are the instructions given to my by smart.

It would be nice to have a simpler fix that wont get broken with a major update.

thanks
bj



Hi BJ,

Thank you for your response.
 
I have consulted with the product specialist again about this issue. I have provided a possible fix below.
 
NOTE: SMART does not officially support Ubuntu 10.04.
 
NOTE: The actions in this script may void any commercial support which you may have purchased.
 
NOTE: This should only be attempted by a qualified system administrator.
 
When connecting a SMART interactive product on a Linux distribution with kernel
2.6.30 or greater, the mouse cursor will always jump to the top left corner of the display. These instructions will fix that issue.
 
These instructions do not apply to a particular Linux distribution. But it is only intended for Linux kernel 2.6.30 or greater. You will need to do this every time your distribution releases a kernel update. This method provides you with drivers that are closer to what your system is currently running.
 
1. Download the source code for the Linux kernel. Every distribution does this differently. Consult your distribution's website for details.
 
2. Edit linux/drivers/hid/hid-input.c. In the function
   hidinput_configure_usage() search for:
 
            case HID_UP_DIGITIZER:
                        switch (usage->hid & 0xff) {
 
   Add this code immediately after the switch statement:
 
                                    case 0x00: /* Undefined */
                                                goto ignore;
 
3. Save the file.
 
4. Build and install your kernel according to your distributions instructions.

If you have any further questions or concerns, please contact us again.

---

### Post by Ad@m on 2010-05-21
[http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html](http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html)

This will show you how to compile your own kernel on ubuntu 10.04, but I doubt you wish to tweak the kernel. Hence there is no point issuing the command make menuconfig.

Instead do the following,

gedit drivers/hid/hid-input.c

Scroll down to about line 300 and insert the code as required, for example

[INDENT]case HID_UP_DIGITIZER:
        switch (usage->hid & 0xff) {

       [COLOR=DarkOrchid] case 0x00: /* Undefined */
        goto ignore;[/COLOR]
        
        case 0x30: /* TipPressure */
            if (!test_bit(BTN_TOUCH, input->keybit)) {
                device->quirks |= HID_QUIRK_NOTOUCH;
                set_bit(EV_KEY, input->evbit);
                set_bit(BTN_TOUCH, input->keybit);
            }
[/INDENT] 
Save and exit.

Proceed as normal.

---

### Post by KermEd on 2010-06-09
I put up a few easier methods - this should resolve the issue for you guys :D  Just remember, with ubuntu, use gksudo instead of sudo for gedit.

[http://exchange-forum.smarttech.com/forums/p/6816/15572.aspx#15572](http://exchange-forum.smarttech.com/forums/p/6816/15572.aspx#15572)

---

