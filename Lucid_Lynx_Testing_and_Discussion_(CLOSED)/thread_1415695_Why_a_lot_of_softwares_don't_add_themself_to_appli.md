---
title: "Why a lot of softwares don't add themself to application?"
date: 2010-02-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-25
for instance i'v installed Moto4Lin to try to get my motorola v3x to work and i need to use terminal to use it or create launcher for it or add it manually.

and by the way i have not yet manage to connect my phone to ubuntu.

thanks in advance.

---

### Post by ibuclaw on 2010-02-25
To be added to the Applications panel, the software supplied requires a .desktop file in /usr/share/applications, to be packaged with it. Since most software don't need this - or 3rd party projects don't make these files, hence the reason why they aren't present.

Regards
Iain

---

### Post by fballem on 2010-02-25
> **ibuclaw said:**
> To be added to the Applications panel, the software supplied requires a .desktop file in /usr/share/applications, to be packaged with it. Since most software don't need this - or 3rd party projects don't make these files, hence the reason why they aren't present.

Regards
Iain

**Adding to a menu**

Adding an application to the menu is fairly easy, once you know where the application is installed. Applications seem to install in /opt/x (where x is the name of the application) or in /usr/bin. There may be other places as well. You can use Nautilus to find the application file and any images that can be used.

The following is a sample set of instructions for adding LightScribe to the menus (I put it under Accessories). This assumes that LightScribe has been correctly installed.

*Sample instruction to add LightScribe to the menu System.*

Once installed, then a menu option can be created to use the software.

1. Right-click on Applications and select Edit Menu from the context menu.
2. Click on Accessories, which is where the lightscribe menu item will be placed.
3. Click the New Item button, and enter the following information into the fields:
	a. Ensure that Type is set to Application.
	b. Name may be anything. I use LightScribe Labeler.
	c. Command is: /opt/lightscribeApplications/SimpleLabeler/SimpleLabeler (the browse button may be used to locate the application, which is in the /opt/lightscribeApplciations/SimpleLabeler folder.
	d. Comment may be anything. I use Writes a label on Lightscribe-enabled discs
	e. Click on the icon and browse to /opt/lightscribeApplications/SimpleLabeler/content/images folder. Once browsed, a list of suitable icons appears. Select one.
	f.  Click on the Close button, which will complete the application.

To use, select the launcher from Applications > Accessories > LightScribe Labeler (or whatever was put in the Name field.

*end of sample instructions*

I hope this helps,

---

### Post by aviramof on 2010-02-25
thank you very much you have helped me a lot.:)

---

