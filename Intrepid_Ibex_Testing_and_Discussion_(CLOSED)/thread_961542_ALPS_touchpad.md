---
title: "ALPS touchpad"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by orgrimdoom on 2008-10-28
Hi i have a ALPS touchpad and i have created a fdi file for it to allow use of SHMConfig so i can turn my touchpad off (i use a mouse) and the SHMConfig fdi file doesnt seem to have any effect on gsynaptics or my touchpad

i put the following into the fdi file /etc/hal/fdi/policy/shmconfig.fdi

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="AlpsPS/2 ALPS GlidePoint">
   <merge key="input.x11_options.SHMConfig" type="string">true</merge>
  </match>
 </device>
</deviceinfo>
```

and i get the following from a xinput list in a terminal

```
"AlpsPS/2 ALPS GlidePoint"	id=3	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
```

---

### Post by wgrant on 2008-10-28
You shouldn't, but might, need to restart HAL and X - probably best to reboot.

---

### Post by orgrimdoom on 2008-10-28
I first did a CTRL ALT BACKSPACE to restart X and attempt to turn it off but i get the error about SHMConfig using all tools (synclient syndaemon gsynaptics)

same after a reboot

is there anything i could be missing or not have done?

---

### Post by wgrant on 2008-10-28
Oh, I see the problem. You put the device name in the driver-matching place. You want to specify that the driver is "synaptics", not "AlpsPS/2 ALPS GlidePoint". The synaptics driver handles more than just Synaptics touchpads.

---

### Post by orgrimdoom on 2008-10-28
originally i had synaptics there and it didnt allow SHMConfig . . i will redo this a little bit later tonight to confirm

---

### Post by orgrimdoom on 2008-10-29
ok my shmconfig.fdi file now shows

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">true</merge>
  </match>
 </device>
</deviceinfo>
```

and i attempted gsynaptics again . . . it gave me the same is SHMConfig on error.

is there any other way to turn of my touchpad (i know xinput is supposed to be able to do something, but i couldnt figure out what command to give it)

---

### Post by orgrimdoom on 2008-10-29
hate to do this but bumping the topic

im not really sure why this doesnt work, could it possibly be the hardware?

im attempting this on a ASUS g2s (disabling the touchpad to use my mouse)
[http://usa.asus.com/products.aspx?modelmenu=2&model=1675&l1=5&l2=61&l3=417&l4=0](http://usa.asus.com/products.aspx?modelmenu=2&model=1675&l1=5&l2=61&l3=417&l4=0)

Thanks
     Orgrimdoom

---

### Post by wgrant on 2008-10-29
I can't tell why it's not working, but why not just disable it in System->Preferences->Mouse->Touchpad?

---

### Post by orgrimdoom on 2008-10-29
system >> preferences >> mousepad brings me to a screen with a general and accessibility tab . . . there is nothing about a touchpad there or disabling any mouse tools

is there any xinput commands i could use w/ the above information to disable it?

ty org

---

### Post by wgrant on 2008-10-30
Erm. Please attach /var/log/Xorg.0.log.

---

### Post by orgrimdoom on 2008-10-30
My xorg log file has the following
[http://pastebin.com/m7ce9e433](http://pastebin.com/m7ce9e433)

---

