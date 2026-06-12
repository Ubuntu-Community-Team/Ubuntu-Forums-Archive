---
title: "A little advice required"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by trendyabinash on 2009-03-19
Sir I am using Intrepid Ibex.

And I connect to internet using the ndisgtk. as my wireless drivers are not present in default so I have use a windows driver.

It is of Marvell, there are many post for it (if you want try searching for mrv8335).

Just want to ask that how can I use the update manager to update to a beta version and will Jaunty support ndisgtk???

I mean I tried kubuntu alpha 5 and it took the driver but didn't connect to the network. It is written in their site that we have to update it once then it will start working but how the hell I can update my system if it doesn't connects to the network?

I prefer gnome and I want to use jaunty alpha so that I can also contribute to the bugs report.

any kind of advice will be full heartedly appreciated.

---

### Post by philinux on 2009-03-19
Simple, no need to install. Just burn and run the live alpha 6 cd.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Test it out see if it connects. If it does not try it wired to update the driver. I would not install without a working internet.

---

### Post by trendyabinash on 2009-03-19
sir what if it doesn't ?, then even after the final release I will have to wired it and install the update, it will be like in hell.

it is really trouble some, to connect to the network.
Why don't the developers create a native driver for it?

---

### Post by trendyabinash on 2009-03-19
I have seen many guys posting for the same device which I have, are there of those who is using it on jaunty?

my device is :-
Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless
and device id is 11AB:1FAA

---

### Post by Bert Mariën on 2009-03-21
I have a broadcom device, But I alsways use a little trick to connect in a new distro.

Just copy the /lib/firmware files for your device to a accessible place. After a new install just copy does files back to the /lib/firmware directory.

When you reboot, it should work, although it might later want to "activate" the driver or upgrade it.

Try it.

---

### Post by Bert Mariën on 2009-03-21
Works for every distro I ever tried.

---

### Post by Bert Mariën on 2009-03-21
Mind you, some distro's usea folder and some use separate files.

---

### Post by Bert Mariën on 2009-03-21
You should find out which uses which.

---

