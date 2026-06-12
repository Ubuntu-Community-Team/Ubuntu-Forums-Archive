---
title: "How to get out of oem modus"
date: 2023-11-15
forum: Installation &amp; Upgrades
---

### Post by elisabethroben on 2023-11-15
Dear Ubuntu community,

I purchased a new computer with pre-installed Ubuntu.
Unfortunately, when starting it, it did not ask me to install Ubuntu as it is normally done.
I set up a user profile under my name and gave myself administrator rights, but the computer never even asks for which user it should boot.
Whatever I do is under oem, and this causes real problems. I cannot access properly my documents, it does not always save what I do, and it never requires a password for anything I do in terminal.

I searched a bit on the Net, but I only found people wishing to set up oem, never anyone who wished to get out of it.

Anyone can help me?

Thanks a lot in advance,

Eva (not Elisabeth, my daughter meddled with my gmail account...)

---

### Post by MAFoElffen on 2023-11-15
When a computer is pre-installed with Ubuntu, using the OEM type installation, on the first boot, it asks the user for the UserName and password, then some other UserData & basic preference kinds of questions...

You can get to "Settings" from the menu in the top right of the Top Bar. In "Settings" go to "Users"

Does that show multiple Users besides your account?

---

### Post by yancek on 2023-11-15
The link below gives a brief explanation of what to do on an initial boot of an OEM install, down the page under Part 2.  A more detailed explanation is available at the 2nd link below.

[https://askubuntu.com/questions/1386806/what-is-oem-installation-regarding-linux-distributions](https://askubuntu.com/questions/1386806/what-is-oem-installation-regarding-linux-distributions)

[http://iso.qa.ubuntu.com/qatracker/testcases/1305/info](http://iso.qa.ubuntu.com/qatracker/testcases/1305/info)

Do you have autologin available?  Check System Settings/ Users.

---

### Post by grahammechanical on 2023-11-15
This will sound like a silly question, but have you rebooted?

I have purchased two laptops with Ubuntu pre-install as an OEM install. On the first boot the buyer is allowed to set certain such as location and language. The buyer can also set a user name and password. On the next boot the machine should load to a log in screen showing just one user whose password will allow the operating system to load to the desktop. This process should remove the supplier's user name and password.

Regards

---

### Post by elisabethroben on 2023-11-16
Dear MafoElffen, Yancek and Grahammechanical,

thank you so much for your returns.
1) Yes, I have rebooted, but it didn't change anything. It rebooted in oem modus and didn't allow me to select myself as user.
2) I went to settings initially and set up my user profile. Then I had that profile, but couldn't access it, because the system rebooted all the time in oem modus.
3) Finally, I went into boot manager and clicked on "booting as ubuntu" (there was only that selection, with oem as an under-modus I couldn't click on; not that I would have wanted). That made the computer switch to my normal user name and password.
4) Then I found out that all my data was unaccessible, because I had transferred all my files from my old computer to this one, but when it was still in oem modus.
5) I cannot remember how I did it, but with some trial and error I managed to access these files from my normal user account in order to move the entire oem there., and then I moved all folders under oem to my user account.
6) Now there is an oem folder in my personal folder, but it is empty. 

I did not go to the links you sent, Yancek, but I suppose I should do that in order to purge the computer coherently from oem and get rid of it completely.

Thanks again!

Eva

---

### Post by SeijiSensei on 2023-11-16
I wouldn't futz with this much longer. Just download a 22.04 version of some Ubuntu flavor and put it on a USB stick. Boot from that stick and choose "Try Ubuntu." Does it have everything you were expecting? If so, I'd overwrite the OEM version.

[https://ubuntu.com/tutorials/install-ubuntu-desktop](https://ubuntu.com/tutorials/install-ubuntu-desktop)

---

### Post by MAFoElffen on 2023-11-16
Since I was a Certified Onsite Warranty Technician, and also an IT Consultant, I have a little different perspective.

"First", since it is new and under "Warranty", contact the Support of the Vendor you bought it from, to see what they want to do. The OS was pre-installed and it needs to be reloaded (reinstalled) to correct it. Tell them "it is stuck in a boot loop, stuck in the OEM Setup process, and will not get out if it". They may have you return it for another, or let you reinstall the OS yourself, with their guidance.

Refer to this thread. many Vendors tell their customers to come here for OS Support. Then tell them that we recommended you to contact them for "product support", and refer to this thread. They want a good review of their products and service. Let their system work for you.

Whatever their procedure is, they should be "kept in the loop" to keep your new machine under warranty. If they tell you that you can reload it, many vendors will overnight a LiveUSB already setup with their approved install image. While others may want to ship a blank USB Flash Drive, which is not feasible for some customers if they do not have another computer, to download from Ubuntu, and setup the installer image... But if they do, we can help with instructions. Just so whatever, is approved by them, and they document it in your warranty notes.

Many vendors are willing to do this, because it is cheaper, than the shipping cost of sending it to Depo, or sending you another Laptop, and having to sell an open-box item.

Keep your computer under warranty and let the support system of your vendor working correctly. In the long-run, that is in your best interest.

Keep this thread open until that it done. We are patient and will be here to answer any questions about that until this is resolved. Please keep us updated what they decide, and if you need any help.

Crossing my fingers that their process is efficient and timely.

---

### Post by yancek on 2023-11-16
I would suggest you go to the links in my earlier post for the purpose of understanding what you have.  If you are now able to boot and access your newly created user files, there would not likely be a need to do anyting further.

---

