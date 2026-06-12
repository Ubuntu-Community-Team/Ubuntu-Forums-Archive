---
title: "(SOLVED) Printer fails to print test page"
date: 2021-05-08
forum: Installation &amp; Upgrades
---

### Post by fkrogh2 on 2021-05-08
Printer is a Samsung M262x 282x Series.  When trying to print a test page it gives an audible click, and later another click when if gives up waiting.  Any Ideas, the printer worked before a new install.  Thanks,
Fred

---

### Post by fkrogh2 on 2021-05-09
I know a tiny bit more.  The back of the printer says "Model: Xpress M2625D.  lsusb gives
Bus 007 Device 004: ID 04e8:331e Samsung Electronics Co., Ltd M262x/M282x Xpress Series Laser Printer
And if I print a self test page, it says "%%%% If you can read this, you are using the wrong driver for your printer."
CUPS, is using
[TABLE]
[TR]
[TH]Description:[/TH]
[TD]Samsung M262x 282x Series[/TD]
[/TR]
[TR]
[TH]Location:[/TH]
[TD]Fred's Office[/TD]
[/TR]
[TR]
[TH]Driver:[/TH]
[TD]Samsung M262x 282x Foomatic/lj5gray (grayscale)[/TD]
[/TR]
[TR]
[TH]Connection:[/TH]
[TD]usb://Samsung/M262x%20282x%20Series?serial=ZEM3BJCF9000EKB[/TD]
[/TR]
[TR]
[TH]Defaults:[/TH]
[TD]job-sheets=none, none media=na_letter_8.5x11in sides=one-sided[/TD]
[/TR]
[/TABLE]
 
Unfortunately I'm still unclear on how to proceed further.   Thanks,
Fred

---

### Post by kurt18947 on 2021-05-09
I have a Samsung MFD as well. I've had better luck using the Samsung printer driver located on HP's support web site. HP bought Samsung's printer business. This might get you pointed in the right direction. I don't think the model matters; there's only one universal driver afaik.

[URL="https://support.hp.com/us-en/drivers/selfservice/samsung-xpress-sl-m2870-laser-multifunction-printer-series/16462897"]https://support.hp.com/us-en/drivers/selfservice/samsung-xpress-sl-m2870-laser-multifunction-printer-series/16462897

[/URL]You do have to make the files executable if they aren't. I'm using this driver on Ubuntu 20.04. The only glitch I've found is that to scan I must first
'wake' the machine up then launch the scanning software. It does work.

---

### Post by fkrogh2 on 2021-05-10
Thanks for pointing me toward HP.  I couldn't get anything useful off their web site ([https://support.hp.com/us-en/drivers/selfservice/samsung-xpress-sl-m2625-laser-printer-series/16462833/model/16462837](https://support.hp.com/us-en/drivers/selfservice/samsung-xpress-sl-m2625-laser-printer-series/16462833/model/16462837)), but in cups, I selected HP as the manufacturer and after several tries HP 2563 Foomatic/p2563 (recommended) prints.  But it does not print double sided.  Tried the website again, selected something that looked like my printer and saved the tar file instead of trying to work with it in another way.  Unpacked it, deleted my old printer, ran the install, selected a default for two sided printing (need to do this), and I have my printer back.  Many thanks.

---

