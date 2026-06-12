---
title: "Installation problem"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by polskimoose on 2010-05-28
Ok I'm desperate.  So i got a Dell Dimension E310 desktop that some guy was gonna throw out.  so i'm trying to install ubuntu on it.  i made a 10.04 boot disc, and i have it on there. only when i go to the boot menu, its not listed as an option. my only two options are:

*Onboard SATA Hard Drive
*Onboard or USB CD-ROM Drive

When i select the first option, it takes me to windows, which gets the blue screen of death within thirty seconds. when i select the second, it says "Selected boot device not available."

please help me, i really need to get this computer working.

---

### Post by polskimoose on 2010-05-29
pleas help, anyone?

---

### Post by howefield on 2010-05-29
You have made an Ubuntu Live CD, yes ?

Downloaded the iso file, checked the MD5SUM and burned to cd as an image, not a data file ?

---

### Post by polskimoose on 2010-05-29
yes i have, and i know it works because when i put it in a different windows computer it works.  im not sure what MD5SUM means though.

---

### Post by howefield on 2010-05-29
> **polskimoose said:**
> im not sure what MD5SUM means though.

Checking the MD5SUM is a method with which you check the integrity of your download and burned CD, but that would seem a moot point, given that you are successfully using it in another machine. 

So you have a good CD, and can select to boot from the CD but doing so gives you an error message. Could be faulty CD drive.

Is it possible to boot from USB ? 

Create on your other machine, an USB install using Startup Disk Creator from the System > Administation menu.

---

### Post by polskimoose on 2010-05-29
could i do that with windows?

---

### Post by howefield on 2010-05-29
> **polskimoose said:**
> could i do that with windows?

Not exactly, you could boot your other machine with the Ubuntu live cd and make the USB Startup Disk using the iso file which you would need to have access to, eg, on the windows drive.

---

### Post by polskimoose on 2010-05-29
no i mean could i make the boot USB using a windows machine?

---

### Post by krishnandu.sarkar on 2010-05-29
You can also install ubuntu from windows also using Wubi. 
And yes you can make LiveUSB in Windows.

---

### Post by darkod on 2010-05-29
> **polskimoose said:**
> no i mean could i make the boot USB using a windows machine?

Yes, look here in section 2. Select USb Stick and Windows, click on Show me how for detailed instructions.
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by darkod on 2010-05-29
> **krishnandu.sarkar said:**
> You can also install ubuntu from windows also using Wubi. 


Forget about wubi. Make a proper installation. You CAN NOT install ubuntu from windows. You CAN install wubi inside windows, that's not ubuntu working on its own partition.
And wubi is not designed to be a long term install, only a quick try. So if you plan using it for long time, it will start having issues after a while.

---

### Post by howefield on 2010-05-29
> **krishnandu.sarkar said:**
> You can also install ubuntu from windows also using Wubi.

Useless info, did you read the first post ;)

@OP, have a browse here

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by polskimoose on 2010-05-29
> **krishnandu.sarkar said:**
> You can also install ubuntu from windows also using Wubi. 
And yes you can make LiveUSB in Windows.

yeah but windows on that desktop blue screens. im gonna try the USB though

---

