---
title: "16 HP 250 G4 weak wireless signal"
date: 2016-06-11
forum: MINT
---

### Post by Alan_Macdonald on 2016-06-11
Hi. I have the same issue on the exact same model of laptop.  I am on Linux Mint 17.3 but ran the command.  Since it's an Ubuntu derivative I was hoping it would be the same fix.  I have attached the output.  What should I try now?

thanks

[ATTACH]269518[/ATTACH]

---

### Post by howefield on 2016-06-11
Post moved to own thread and moved to the "*MINT*" sub forum.

---

### Post by jeremy31 on 2016-06-11
```
sudo apt-get install git build-essential
git clone https://github.com/lwfinger/rtlwifi_new
cd rtlwifi_new
make
sudo make install
echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

Reboot
Now we can play with a new module parameter and see if we can improve the signal
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=1
iwlist scan | egrep -i 'ssid|quality'
```
Then we check the second option to find which one works better
```
sudo modprobe -r rtl8723be
sudo modprobe rtl8723be ant_sel=2
iwlist scan | egrep -i 'ssid|quality'
```

If ant_sel=1 is better
```
echo "options rtl8723be ant_sel=1" | sudo tee -a /etc/modprobe.d/rtl8723be.conf
```

If ant_sel=2 is better
```
echo "options rtl8723be ant_sel=2" | sudo tee -a /etc/modprobe.d/rtl8723be.conf
```

---

### Post by Alan_Macdonald on 2016-06-13
Ah the forum didn't inform me you replied despite me subscribing to the thread.  I found this [http://ubuntuforums.org/showthread.php?t=2304607&page=2](http://ubuntuforums.org/showthread.php?t=2304607&page=2) and specifically post #17 and have had to open up the case and physically swap the wifi cable from one connector to another.  This solved the problem in Mint but I am dual booting with Windows 10, so booting into Windows 10 now had the problem I originally had in Linux i.e. has to be really close to the wifi signal to work, which is sub-optimal to say the least.

I'll try moving the cable back to the original connector and try your solution.  Was really hairy and not ideal for a new laptop so I will try again tomorrow or next day and report back.

Thanks for your help!

---

### Post by jeremy31 on 2016-06-13
I don't know how easy or difficult that laptop is to take apart but a second antenna would solve the issue.  I think they are available and fairly cheap

---

### Post by Alan_Macdonald on 2016-08-07
Finally got round to trying this.  I moved the antenna physically back to position 1 which works fine in Windows and then performed these steps and it works!  Thank you so very much.

For anyone else who comes across this there was a "be" missing from the modprobe commands that set the antenna number:


sudo modprobe rtl8723 ant_sel=1

should have been:
sudo modprobe rtl8723be ant_sel=1

---

