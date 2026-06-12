---
title: "LJ-4 PPD file ????"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by Hank Montgomery on 2007-07-02
OK, I did something stupid in trying to install a printer for the first time.
I did what seemed to be a straight forward install of a printer - very similar to windows.
But the printer (LJ4) "data" light stays blinking and nothing will print.

Searching for help I followed some wrong instructions:
I am running ubuntu 6.05 but the instructions were actually for 5.10.
I did :
$ sudo rm /usr/share/cups/model/hplip
and
$ sudo sed -i 's/HP (HPLIP)/HP/' /usr/share/ppd/hplip/*

After which I could not even add a new printer.

So.....

I reinstalled the CUPSYS package and can now add the printer but it still doesn't work.

Then instead of taking the default that NEW PRINTER suggests (hpijs) I tried "ljet4".
But when I click "Install Driver" it pops a screen looking for the location of a "PPD File".

What is a PPD file and how do I find one?????


====    UPDATE   =====
I GIVE UP!!
I'll put up another windows machine for my printint !!!!


After wading through half a dozen forums and multiple attempts to find decent documentation -
It appears I don't need a PPD file !
It appears that the PPD file is only needed to install a NEW driver !
Therefore I don't need to click the "install driver" button if the driver is listed for selection.
Dumb me thought it meant to install the selected driver - 
I guess anyone should know that the"install driver" button next to the selection box 
   is not to be used to install the selected item !!

BUT - Even after reloading every HP package I can find on the system, it still isn't working !!
There is a selection of 3 drivers is provided.
I tried all 3 but NONE of them work.
If the printer does anytning at all it prints garbage.
And some times I can't even add a printer because the software does not find a port.
At this point I don't know if it's a software or hardware problem - 
  but in either case THE SOFTWARE STINKS !!!

And what die I learn by searching for information -
There seem to be a LOT OF PRINTER PROBLEMS -
   AND NOT MANY ANSWERS !!

I GIVE UP.

---

