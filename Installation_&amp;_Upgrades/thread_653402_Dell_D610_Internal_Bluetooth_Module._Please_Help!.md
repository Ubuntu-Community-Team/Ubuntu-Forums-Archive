---
title: "Dell D610 Internal Bluetooth Module. Please Help!"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by Mikethaninefive on 2007-12-29
Ok, first off- i apologize if this is a silly question or posted in the wrong 
spot. That being said I have a Dell latitude D610 with an internal Bluetooth module (350) I just switched last night to Ubuntu and I'm loving everything except I can't figure out how to install or if it is installed or whats going on with my Bluetooth. I have a Nokia E62 the Bluetooth is enabled on the phone but when I use the phone to scan for devices none are found. The BT light is lit steadily on the comp. There is an Icon for BT manager on th top bar, I've looked in the device manager and can't find any BT devices, ARRRGGG please help, this is driving me bannanas b\c I've searched the forums and google the bejesus out of it but I can't find anything!  Oh yeah, I'm running Gutsy Gibbon 7.10. Thank's in advance.

---

### Post by Mikethaninefive on 2008-01-11
Man! 36 views and not even any comments? Please help, even if you can't help post a reply so at least I know that I'm not the only one or if it's a D610 thing. Thanks

---

### Post by SingingWing on 2008-01-11
> **Mikethaninefive said:**
> Man! 36 views and not even any comments? Please help, even if you can't help post a reply so at least I know that I'm not the only one or if it's a D610 thing. Thanks

For an external bluetooth device to find a computer for file transfer to Ubuntu the obex-server needs to be running. Go to System/Preferences/Sessions and add a startup program. Call it something like Bluetooth File Transfer Listener and make the command gnome-obex-server. Reboot.

To find your computer from a phone then you must turn on bluetooth discovery in the Bluetooth Preferences applet.

Good luck,
-- 
Steve

---

### Post by rabbito on 2008-01-12
Mike, i dont have a solution for you but you do have a possible answer for me :) I just picked up a Dell D610 and could not really find a post with someone using 7.10 on it until you. Did everything work out of the box? I would think after enabling some repositories everything should be covered but the main thing is for wireless to work.

*edit*

I dont know which wireless card mine has as i have not gotten it yet but mine has the Intel GPU and the 1400x1050 res support

---

### Post by SingingWing on 2008-01-12
My Dell Inspiron 9400 bluetooth worked with Gutsy with an internal Dell Truemobile 355 bought off Ebay. Only tweaking was to add the gnome obex file server to the system startup to support transfer TO the pc.
-- 
Steve

---

### Post by Ralph L on 2008-01-20
I also have a Dell Latitude D610 with a 350 Bluetooth module and am running Gutsy.  I am trying to send pictures to the computer from the Nokia phone with Bluetooth.  While a I get a Bluetooth symbol in the taskbar panel and the blue light comes on steady, I can't get the computer to respond to the phone.  

I tried the solution suggested by SingingWing above but it still didn't work.  I would appreciate very much any help I could get on this.

Ralph

---

### Post by Ralph L on 2008-01-20
> **rabbito said:**
> Mike, i dont have a solution for you but you do have a possible answer for me :) I just picked up a Dell D610 and could not really find a post with someone using 7.10 on it until you. Did everything work out of the box? I would think after enabling some repositories everything should be covered but the main thing is for wireless to work.

*edit*

I dont know which wireless card mine has as i have not gotten it yet but mine has the Intel GPU and the 1400x1050 res support

Rabbito

I have a Dell Latitude D610 on which I am running Gutsy.  I started with Edgy and then upgraded to Feisty, then to Gutsy.  The only thing that worked out of the box with Edgy was Ethernet.  The touchpad was unusable, it was so slow.  I found some settings for /etc/X11/xorg.conf that fixed the problem.  I can send them if you want.

The USB connection to my HP Photosmart C6180 almost worked right.  However, I had wounded my OS trying to get the touchpad working and had to reload everything.  But then it worked.

The wireless network didn't work because of the Broadcom chip, but again I found a real good fix on the forum.  It uses ndiswrapper.  I can also reference you to that.

I still can't get my wifi printer to work over the network.  I have been getting some advice through Launchpad.

I am having trouble moving DVD R/W between XP and Ubuntu.  I am suspicious that they use different formats, but I don't know yet.

And I can't get Bluetooth running.

I haven't tried email yet, nor have I tried networking with other computers.  I have a Vista computer with which I would like to network.

I will give you any help I can and would appreciate the same.

Ralph

---

### Post by Mikethaninefive on 2008-02-20
Dang! Sorry I have not replied, I used to get emails when I got a reply but I hadn't gotten any. As of now  
I have not tried any of the solutions yet but I will. I appreciate all the help so far! Right now I'm tackling a different issue- I tried to hook up my notebook to my TV via S-video and, failed miserably. Now I can only use a CRT monitor and I can't figure out how to switch it back to the LCD. I tried the hotkeys but the CRT just goes blank and I can't see anything on either till I switch again with the hotkeys. lol, even with all this I'm still glad I switched. :) Oh and to Rabbito everything went great, the only thing I can't get to work is BT.

---

