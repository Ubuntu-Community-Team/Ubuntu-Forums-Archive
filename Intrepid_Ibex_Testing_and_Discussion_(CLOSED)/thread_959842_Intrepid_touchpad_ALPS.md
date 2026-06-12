---
title: "Intrepid touchpad ALPS"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by orgrimdoom on 2008-10-26
I have a asus g2s and i am trying to disable the touchpad, my current approach is gsynaptics to disable it, as its what ive used in the past :)

when i run gsynaptics i realized that i need to reset my SHMConfig and attempt to figure out the new way of modifying hardware so i made a file named shmconfig.fdi inside the /etc/half/fdi/policy/ folder with the following inside it

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

here is the result of xinput

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

this does not seem to enable SHMConfig for my touchpad, althou on various google searches i have come to the conclusion that it should, is there anything im missing? :)

ty orgrim

---

