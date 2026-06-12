---
title: "adb commands work only with ./adb"
date: 2014-11-08
forum: Installation &amp; Upgrades
---

### Post by charitosha on 2014-11-08
So i had to re-install adb, thought that since i had installed once i wouldn't have any problems.... well half-way i stumbled upon problem.
The phone is checked at the usb-debugging and even checked in the unknown sources(under application setings).
Since i have 12.04 32 bit i didn't installed ia32-libs. oracle java 7 is installed.
I've downloaded adt-bundle-linux-x86-20140702.

_*The main problem is the following: until now adb commands works under one condition only.*_
*I have to cd in the terminal to the platform-tools folder and then to use ./adb. If simply adb will be used i will get command not found...*
As far as i know when "." is used in front of a file then that file is hidden... why did that happened?

For my PATH variable i used:
```
nano ~/.bashrc
```
and at the end of the file i typed:
```

#AndroidDev PATH
export PATH=${PATH}/home/haris/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/tools
export PATH=${PATH}/home/haris/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/platform-tools

```
that ~/.bashrc file is saved in /home/haris/.bashrc

Now my declaration of the udev rules works correctly but only declared 1 device. 

_*By the way my second and last question*_: How is it possible to make udev rules for random devices, so that you won't have to every time to use the vendors id and product id and make a specific udev rule for each and every device that you'll plug-in

---

### Post by nerdtron on 2014-11-08
./adb - the dot-slash (./)  means "on this folder, the file adb" which will run the script (if it is a script/program)
.adb - a file with a dot at the start is a hidden file.

Back to the problem, your export command seems to have a typo, the default paths (and additional ones) are separated by a colon:
```
kenneth@nerdtron:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games 
```

So if you need to add a custom path to the PATH variable you need to:
```
export PATH=YOUR_PATH_WITHOUT_TRAILING_SLASH:$PATH
```
Reboot to reset you current changes so far, then try adding custom path again. To verify if your path is added, just use the echo command that I used above.

---

### Post by charitosha on 2014-11-08
About the trailing slash, you mean the "android_dev_tools"???
Also your echo $PATH code confused me a bit...

Look:
i)Open the terminal inside platform-tools folder:
```

haris@Mini-210:~/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/platform-tools$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games/home/haris/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/tools/home/haris/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/platform-tools

```
ii)open terminal inside tools folder:
```

haris@Mini-210:~/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/tools$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games/home/haris/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/tools/home/haris/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/platform-tools

```

although the paths should show 2 different destinations, it shows the same... what???

However if open the terminal in the sdk folder and use readlink:
```

haris@Mini-210:~/android_dev_tools/adt-bundle-linux-x86-20140702/sdk$ readlink -f tools
/home/haris/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/tools
haris@Mini-210:~/android_dev_tools/adt-bundle-linux-x86-20140702/sdk$ readlink -f platform-tools
/home/haris/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/platform-tools

```

P.S. or by trailing slash you mean the "/" sign? :?:

---

### Post by nerdtron on 2014-11-08
> trailing slash you mean the "/" sign?
Yes.

Your current "echo $PATH" is wrong. There should be a colon ( : )between the 
**/usr/games **folder and the [B]/home/haris/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/tools/home/haris/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/platform-tools

[/B]Look carefully on the separation of paths.

---

### Post by charitosha on 2014-11-08
Ok i managed to do it! Thank you for the help!
I put the colon ( : ) between usr/games folder and the other 2 corresponding folders and it worked.
However it makes me wonder:
```

haris@Mini-210:~$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/haris/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/platform-tools

```
Now it showed the colon ( : ) at the proper place, but why did it showed the specific path and not the path to my user folder or something?

---

### Post by nerdtron on 2014-11-08
Because of your wrong export command with no colons.
```

#AndroidDev PATH
export PATH=${PATH}/home/haris/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/tools
export PATH=${PATH}/home/haris/android_dev_tools/adt-bundle-linux-x86-20140702/sdk/platform-tools
```

Those line basically means combine the current PATH and add the path you specified, but since you did not specify any colon as a form of separation, it just assumed that it is a valid path the you declared. It won't bother to check so your custom path will just be appended on the last entry which will have a discrepancy on the final output.

---

