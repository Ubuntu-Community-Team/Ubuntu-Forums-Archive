---
title: "Mint 17 Touchscreen not working?"
date: 2018-03-06
forum: MINT
---

### Post by RallyDarkstrike on 2018-03-06
[I][COLOR=#ff0000]Hi all - I have an HP Pavilion Touchsmart 14 laptop running Linux Mint 18.3 MATE, which is Ubuntu based. Everything on the laptop functions great, except the touchscreen, which does not work at all under Linux.

I've done some searching and apparently this laptop is Ubuntu certified, including the Elan Touchscreen it has ( [/COLOR][[COLOR=#ff0000]https://certification.ubuntu.com/catalog/component/usb/2113/04f3%3A0247/[/COLOR]]("https://certification.ubuntu.com/catalog/component/usb/2113/04f3%3A0247/")[COLOR=#ff0000] ), so curious why the touchscreen is not simply working out of the box? I know Mint ISN'T Ubuntu, but it uses a lot of Ubuntu repositories and drivers.

Any help on getting it working would be appreciated! :)[/COLOR][/I]

EDIT - Ignore the above - it's been a year since I looked into trying to get the touchscreen working and running a xinput --list gives me:

```
 Virtual core pointer                    	id=2	[master pointer  (3)] &#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=12	[slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. eGalaxTouch EXC7910-1018-13.00.01	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; HP Truevision HD                        	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=13	[slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                     	id=14	[slave  keyboard (3)]


```

My touchscreen is an eGalax, apparently. Still no luck getting it to work so far though! :(

---

