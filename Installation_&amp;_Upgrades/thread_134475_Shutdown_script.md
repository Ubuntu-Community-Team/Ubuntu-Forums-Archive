---
title: "Shutdown script?"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by tgcUbuntu on 2006-02-22
I frequently have an iPod plugged into my computer. When I shutdown the computer I sometimes forget to eject it first. I'm thinking that I could create a script that would check to see if it's mounted and if so eject it before the computer shuts down.

Is there some place where you can specify a script to be executed on shutdown?

Thanks,
Ted

---

### Post by Killgore on 2006-02-22
You could try BUM (Boot-Up Manager) but i dont see why it matters if it is still mounted. Ubuntu will unmount everthing before shutting down so if you take a USB device out when the computer is off it can do no damage to the device.

---

### Post by jchau on 2006-02-22
I think the folder /etc/rc6.d holds the scripts for shutdown.

---

### Post by audax321 on 2006-02-22
Yeah, that eject thing confuses a lot of people. It's only there to make sure that the device is not being written to when you unplug it. After shut down you can unplug/plug the device as you wish. Even when the computer is on and there is no activity on the USB device, you can unplug it and it won't cause any damage, but for mental sanity it's normally better to unmount/eject it ;)

---

### Post by tgcUbuntu on 2006-02-22
I've had to unplug it any number of times when I didn't eject it first. Although the iPod keeps on working without any problems, it always bothers me a little when I still see the "Do not disconnect" on the 'pod.

It seems like there ought to be an easier way to do things at shutdown, after all it's already set up to do things at startup via System->Sessions->Startup Programs.

---

### Post by dickohead on 2006-02-22
I agree, there should be a way to run tasks as shutdown, like backing up of vital data to a network drive, archiving data locally etc, would be very handy!

Not that "crontab -e" isn't a good way too, but gui's are lovely!

---

### Post by sdb2028 on 2006-02-23
Not ttrying to hijack your thread, but how do you get the system to actualy shutdown the computer?
I have a Toshiba Satelite Laptop, when I click shutdown- it shits the system down but I have to manually shut down the computer power.
Any ideas?

---

### Post by audax321 on 2006-02-24
[QUOTE=sdb2028]Not ttrying to hijack your thread, but how do you get the system to actualy shutdown the computer?
I have a Toshiba Satelite Laptop, when I click shutdown- it shits the system down but I have to manually shut down the computer power.
Any ideas?[/QUOTE]

Try taking a look here: [http://ubuntuforums.org/showthread.php?t=277](http://ubuntuforums.org/showthread.php?t=277)

Passing nolapic to the kernel at boot worked for them.


Also check here: [https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)
under the sections marked Canonical Supplied and Community Supplied to see if you can find the specific model of your laptop and see how other people have worked with it and Ubuntu.

---

### Post by sdb2028 on 2006-02-24
Thanks, went there and try'd it---- didn't work.

---

