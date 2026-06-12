---
title: "Trust work tablet 200 (Aiptek) on Karmic problem"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by markkupaakkonen on 2009-10-26
Hi, I would like to get this old tablet of mine working for my daughter.
I think I should add something on my /etc/hal/fdi/policy/10-aiptek.fdi
but what?

Here is what I've got in it now :

```
<?xml version="1.0" encoding="UTF-8"?> 
<deviceinfo version="0.2">
  <device>
    <match key="info.product" contains="Aiptek">
      <merge key="input.x11_driver" type="string">aiptek</merge>
      <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
      <merge key="input.x11_options.USB" type="string">On</merge>
      <merge key="input.x11_options.Type" type="string">stylus</merge>
      <merge key="input.x11_options.Mode" type="string">absolute</merge>
<merge key="input.x11_options.zMin" type="string">0</merge>
<merge key="input.x11_options.zMax" type="string">511</merge>
    </match>
  </device>
</deviceinfo>
```

My xinput --list

```

---
"Aiptek"	id=9	[XExtensionPointer]
	Type is Stylus
	Num_keys is 32
	Min_keycode is 8
	Max_keycode is 39
	Num_buttons is 5
	Num_axes is 5
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 2999
		Resolution is 14763
	Axis 1 :
		Min_value is 0
		Max_value is 2249
		Resolution is 14763
	Axis 2 :
		Min_value is 0
		Max_value is 511
		Resolution is 512
	Axis 3 :
		Min_value is -128
		Max_value is 127
		Resolution is 256
	Axis 4 :
		Min_value is -128
		Max_value is 127
		Resolution is 256

```

And lsusb

```
Bus 002 Device 004: ID 08ca:0010 Aiptek International, Inc. Tablet

```

At this point, there's only cursor moving, and Gimp recognizes the tablet but that's all, can't draw with it.

Thanks.

Markku

---

### Post by Favux on 2009-10-26
Hi Markku,

It looks like you installed the Aiptek driver through Synaptic since xinput is recognizing the tablet.  What's the tablet name and model number?

We messed around with Aiptek tablets on this thread:  [http://ubuntuforums.org/showthread.php?t=1191826](http://ubuntuforums.org/showthread.php?t=1191826)  There might be a few ideas in there you could use.

The aiptek.fdi we came up with is on post #50 here:  [http://ubuntuforums.org/showthread.php?t=1191826&page=5](http://ubuntuforums.org/showthread.php?t=1191826&page=5)

Just in case you don't know about adding extended input devices to Gimp see near the bottom here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

### Post by markkupaakkonen on 2009-10-26
> **Favux said:**
> Hi Markku,

It looks like you installed the Aiptek driver through Synaptic since xinput is recognizing the tablet.  What's the tablet name and model number?

We messed around with Aiptek tablets on this thread:  [http://ubuntuforums.org/showthread.php?t=1191826](http://ubuntuforums.org/showthread.php?t=1191826)  There might be a few ideas in there you could use.

The aiptek.fdi we came up with is on post #50 here:  [http://ubuntuforums.org/showthread.php?t=1191826&page=5](http://ubuntuforums.org/showthread.php?t=1191826&page=5)

Just in case you don't know about adding extended input devices to Gimp see near the bottom here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

Hi Favux, thanks for advice,

my tablet's name and model number is "Trust wireless design and work tablet 200" and I installed the Aiptek driver via Synaptic. I also tried the aiptec.fdi you mentioned, it didn't work. I do know about adding extended devices to Gimp, I'm using one (wacom intuos) at work on my Jaunty desktop, and my sketchbook is HP tx2z ;) As I mentioned, on my 'kitchen' HP-laptop, that I try to set the old Aiptek tablet up for my daughters, the Gimp recognizes the Aiptek tablet, but that's all, can't draw with it. The cursor moves but you cannot do anything with it.

So, that's it then for the time being, I guess...

Edit. Seems that the stylus is locked to left click and that it also grabs mouse to it. So the stylus selects areas on the screen but cannot release the selection. And to get the mouse working, you have to disconnect the tablet, which restarts x.

Cheers
Markku

---

