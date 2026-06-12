---
title: "Multi touch on Lucid"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hackthrough on 2010-03-25
Hi Guys,
 
I've written a kernel-mode driver for a capacitive multi-touch screen digitizer, can compile and install under Lucid beta release, and its working nicely - as a single point touchscreen.
 
I know my code is generating multi-touch messages, but I can't tell if the OS is getting them.
 
Can anyone confirm whether multi-touch input is enabled by default in the beta release of Lucid? 
 
If not, how do I go about enabling it?
 
As far as I understand the documentation, I need to send ABS_X and ABS_Y events to set the cursor position, and ABS_MT_POSITION events to build gestures.
 
I'm sending the input_events as follows:
 
For any touch status change:
ABS_MT_TOOL_TYPE
ABS_MT_TRACKING_ID
ABS_MT_TOUCH_MAJOR
BTN_TOUCH
 
Touch 1: ABS_X, ABS_Y and ABS_MT_POSITION_X, ABS_MT_POSITION_Y
Touch 2 to 10: ABS_MT_POSITION_X, ABS_MT_POSITION_Y only
 
If my input_events are generated correctly, what gestures would have what effects?
 
I should mention that I'm really really new to kernel development...
 
Thanks in advance :)

---

