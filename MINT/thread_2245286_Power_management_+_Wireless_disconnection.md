---
title: "Power management + Wireless disconnection"
date: 2014-09-22
forum: MINT
---

### Post by Banshee-2007 on 2014-09-22
Hello everyone


I am almost new to Linuxmint, and have encountered several issues with it, which make it not as smooth as MS Windows with me. I am posting here because I Linuxmint is Ubuntu-based and I found no answer in the Linuxmint forums.


1- 
The first is power, as I use the system on a laptop, I need to reduce my power consumption when disconnected from a power source. In windows I can simply set the device to "Power Save" as shown in the link: [http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#7](http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#7)
I searched for a tool to do it, and found Jupiter. I followed the explanations in the links below:
[http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html](http://www.ubuntugeek.com/jupiter-light-weight-power-and-hardware-control-applet.html)
&
[http://www.youtube.com/watch?v=sHQ89jYGM08](http://www.youtube.com/watch?v=sHQ89jYGM08)


However, terminal responded with a message that the software is discontinued as highlighted in the screenshot:
[http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#4](http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#4)


I ignored that, and continued, then ended up with this message ```
 "E: Unable to locate package jupiter" 
``` as highlighted in the terminal:
[http://imgur.com/AsUaGlH](http://imgur.com/AsUaGlH)


Is there anyway to install Jupiter in this case, and if not, is there any other tool that does the job ?!




2- Wireless disconnection sign,
I use usually use wireless connect, and in many casses the Internet diconnets and I restart the router. In Windows I know that the Internet has disconnect from the yellow sign appearing on the icon of the wireless connection which is shown in the link below:
[http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#0](http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#0)


However, in Linuxmint and the other distributions, this does not exist, as shown in the link, and in many cases I just keep refreshing the pages until I discover that the line is disconnected:
[http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#1](http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#1)


Is there any method or tool that can be used  to detect such kind of Internet disconnection in Linuxmint ?!





3- Grub customization
I tried to customize the grub installed on my machine. I found these two web pages with some explanation of timing control, background customization and text color editing.


[http://www.jochus.be/site/2013-02-23/linux/setting-a-splash-image-ubuntu-1110-oneiric-and-grub-199](http://www.jochus.be/site/2013-02-23/linux/setting-a-splash-image-ubuntu-1110-oneiric-and-grub-199)
&
[http://www.thegeekstuff.com/2012/10/grub-splash-image/](http://www.thegeekstuff.com/2012/10/grub-splash-image/)


The timeout control and background changing worked fine with me. However, when I applied the following code to know the version the Grub I have on my computer, the terminal replied with an error as shown in the link below:
```
$ grub-install -v 
```


[http://imgur.com/675I2Zi](http://imgur.com/675I2Zi)


I tried to change the color of the text in the /etc/grub.d/05_debian_theme as shown below :
[http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#3](http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#3)


However, after several attempts with changing the colors, only the normal text color was changed (to "Cyan"), and the menu text color never changed as shown in the picture in the following link:
[http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#2](http://imgur.com/t85hMGM,zeVDroe,WLRXUUN,RaYT5Y9,zGC0Rya,tOPiVTh,efGdmUl,huwwJL2#2)


I searched for more tutorials and explanations on this, but never found anything different than the two tutorials in the links I posted above. Does anybody know what is wrong with my grub ?!




I am so sorry for the long thread, and thanks in advance

---

### Post by slickymaster on 2014-09-22
*Since Mint is not an official Ubuntu flavour I'm moving this thread to the ***Other Operating Systems and Projects*** sub-forum*

---

### Post by varunendra on 2014-09-25
Different (unrelated) questions should be asked in different threads. "Different Threads for Different Topics" is a golden rule for getting optimal help, while making the thread(s) helpful for others too.

Having said that, answers I know -

1- I personally use "powertop". It is in the repository and can be installed from software center or with command -
```
sudo apt-get install powertop
```
It is a commandline tool that runs in a terminal with command "powertop". Among many different settings, it displays the "Good" (optimal) or "Bad" (non-optimal) settings regarding power management on different devices in its last 'Tab' (can be reached by hitting left arrow key once). Pressing "Enter" on a selected setting toggles its state between "Good" and "Bad". Downside is - you need to do this at every boot, as the changes remain effective only for the running session.

Another tool, which sounds better at this job (I haven't personally tested it) is "laptop-mode-tools". Since I haven't personally tested it, can't say how it works, and how well. By its description, it seems to run in the background and handle its job automatically, although it also seems to be adjustable.

2- I don't know of any ready-to-use tools that can do what you want (but I don't know everything). We can do it via manually created scripts, but that's all I can think of. For example, we can create a script that tries to 'ping' your dns or any particular site every few seconds, and when it doesn't get a ping reply, pops up a message to indicate the connection is lost.

3- Perhaps this should be asked and answered in a separate thread. Maybe try in Mint forums first.

---

### Post by tgalati4 on 2014-09-25
I'm running Linux Mint MATE 17 and when you click on the bottom taskbar, "Add to Panel", pick "CPU Frequency Scaling Montior".  It displays CPU speed (800, 1.07, and 1.47 GHz on this crappy Acer latop).  You can also pick the power policy:  conservative, on-demand, performance, power-save. And somewhere in preferences, you can choose the power-policy when on AC versus On-Battery.  It's built-in as far as I know.  In older versions of Ubuntu you had to install a bunch of *cpufreq* utilities.  I'm running an Intel processor, so it may be processor dependent.

And yes, try to keep one question per thread, otherwise it is too difficult to troubleshoot in a forum.

---

### Post by Banshee-2007 on 2014-10-06
> **varunendra said:**
> Different (unrelated) questions should be asked in different threads. "Different Threads for Different Topics" is a golden rule for getting optimal help, while making the thread(s) helpful for others too.

Having said that, answers I know -

1- I personally use "powertop". It is in the repository and can be installed from software center or with command -
```
sudo apt-get install powertop
```
It is a commandline tool that runs in a terminal with command "powertop". Among many different settings, it displays the "Good" (optimal) or "Bad" (non-optimal) settings regarding power management on different devices in its last 'Tab' (can be reached by hitting left arrow key once). Pressing "Enter" on a selected setting toggles its state between "Good" and "Bad". Downside is - you need to do this at every boot, as the changes remain effective only for the running session.

Another tool, which sounds better at this job (I haven't personally tested it) is "laptop-mode-tools". Since I haven't personally tested it, can't say how it works, and how well. By its description, it seems to run in the background and handle its job automatically, although it also seems to be adjustable.

2- I don't know of any ready-to-use tools that can do what you want (but I don't know everything). We can do it via manually created scripts, but that's all I can think of. For example, we can create a script that tries to 'ping' your dns or any particular site every few seconds, and when it doesn't get a ping reply, pops up a message to indicate the connection is lost.

3- Perhaps this should be asked and answered in a separate thread. Maybe try in Mint forums first.


I am sorry man, but I tried to something similar in another forum long time ago, and I recieved a complaint from the admin. But I'll consider your advise next time.

1- I've read online about & tested Laptop mode tools. It seems to be a tool that helps in reducing the power consumption of certain processes of features in the system. On the other hand, I've tried to check about Powertop online. I installed the tool and surfed a little in it. I seems to be more of an administrative tool, rather than power-consumption reduction tool (cpu frequency throttling tool), which helps in monitoring the different processes going on the system and terminating energy-hungry and unnecessary processes. This could be good, but not as efficient and easy to use as the tool found in Windows, which I am looking for a similar thing linux.

2- I am not a programmer or a script writer of any sort, and I am not familiar with these things even, which makes an unviable option for me to go for writing scripts that can detect Internet disconnection. Therefore, I guess I'll be waiting a while, until such a tool is present for Linux.

3- I posted that on Linux Mint forums, and found no reply. I did the same of Linux Forums, and recieved some replys, and still I am following up with the comments and tips provided by the guys there.

Thanks very much for your reply varunendra.



> **tgalati4 said:**
> I'm running Linux Mint MATE 17 and when you click on the bottom taskbar, "Add to Panel", pick "CPU Frequency Scaling Montior". It displays CPU speed (800, 1.07, and 1.47 GHz on this crappy Acer latop). You can also pick the power policy: conservative, on-demand, performance, power-save. And somewhere in preferences, you can choose the power-policy when on AC versus On-Battery. It's built-in as far as I know. In older versions of Ubuntu you had to install a bunch of cpufreq utilities. I'm running an Intel processor, so it may be processor dependent.

And yes, try to keep one question per thread, otherwise it is too difficult to troubleshoot in a forum.


Hi mate, I am running LinuxMint 17 Qiana Cinnamon. I tried that applet, and it seems to suffer a bug, so when I click on it the system freezes for a second, then things run again. When I click on the icon multiple times, as when I click on it and do not make any change, or accidentally click somewhere else then try to click on it a second time, the whole system input devices' drivers would crash and the system would freeze. The only thing I can do then is shutting the PC down from the power button then booting up again. On the other hand, I've tried for two days now, and it does not seem to be tuning up the power consumption much as the Windows tool does, as I tested the battery power drain with two options "Powersave" & "Performance", and the first seemed to be giving me only an average of 30-40 minutes of extra battery life, unlike the signifcant difference I get in Windows. I understand the open source tools will develop, and therefore hope to test something more advance in the future. So far, I am still using the Applet as I see to alternative. Laptop Mode Tools caused some hardware problems for me, especially in controlling the mouse cursor.

You can check about the crash problem in "CPU Frequency Scaling Monitor" in latest comments on the official page of the applet:
[http://cinnamon-spices.linuxmint.com/applets/view/70](http://cinnamon-spices.linuxmint.com/applets/view/70)

Also, you can see some problems of "Laptop Mode Tools" mentioned here under the "6.Common problems" tag:
[http://samwel.tk/laptop_mode/faq](http://samwel.tk/laptop_mode/faq)

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

So, for the first question, I will be trying to convince my self with CPU Frequency Monitor for the mean time, unless it is fixed and I become able to rely on it. For the second the question I do not think that the scripting solution actually fits, especially that I found no other solutions on LinuxMint forums or LinuxFurms. For the third question I am following up with the thread I posted on LinuxForums.

Thanks you guys !

Do you have any other suggestions, or should I mark the topic as solved for the mean time ?!

---

### Post by varunendra on 2014-10-06
> **Banshee-2007 said:**
> 2- I am not a programmer or a script writer of any sort, and I am not familiar with these things even, which makes an unviable option for me to go for writing scripts that can detect Internet disconnection. Therefore, I guess I'll be waiting a while, until such a tool is present for Linux.
Do you really think that we here at *Ubuntu* forums assume that every user (or even one-tenth of *Ubuntu* users) knows scripting? Or even terminal commands?

Any tool, if exists for that, would do the same or almost the same thing, the same way, only possibly providing a relatively easy-to-use frontend. So consider a script such a 'tool' made exclusively for you - on demand. As for not being able to create one yourself, what do you think the geeks here hang out for? We love tinkering, so as long as you have time and patience to possibly do some experimenting before a working solution is found, we'd be glad to help with that (we don't usually do spoon-feeding, but this is different).

Regarding the other points, I have personally experienced and have also confirmed here on the forums many times that using it (changing all the settings to "Good") increases the battery backup around 15% (10 - 20 %, for example increasing the backup time on my laptop from 3:40 to 4:15). CPU throttling, if that's what you want, is done automatically by the kernel depending upon the demand by the applications. I don't see how 'forcing' it can help.

For example, I was once installing Nero 7 suite on an Asus netbook running Windows 7 Home while travelling. It took around 2 hrs. and still was in progress when I finally cancelled it. When I reached the office to where I was going, I connected it to AC power source, and restarted the installation from start. Finished in less than 18 minutes!! Now that's what a 'forced' throttling or any kind of too aggressive power saving does to you. I can't think who can live with that.

On the other hand, if you are doing nothing but a simple text editing, the Linux kernel (provided you have suitable drivers, especially graphics) will throttle it down to just the level that I guess the Windows 7 'tool' had done in the above case.

Regarding 'Grub Customization', feel free to start a new thread here at Ubuntu Forums if you haven't already. Just make sure to mention 'Mint' so people know what they are dealing with. These are things what we have this "Other OS" section for.

Not trying to compel you to try something, just sharing some experience I have and letting you know of the options we can make available if you want.

---

### Post by Banshee-2007 on 2014-11-02
> **varunendra said:**
> Do you really think that we here at *Ubuntu* forums assume that every user (or even one-tenth of *Ubuntu* users) knows scripting? Or even terminal commands?

Any tool, if exists for that, would do the same or almost the same thing, the same way, only possibly providing a relatively easy-to-use frontend. So consider a script such a 'tool' made exclusively for you - on demand. As for not being able to create one yourself, what do you think the geeks here hang out for? We love tinkering, so as long as you have time and patience to possibly do some experimenting before a working solution is found, we'd be glad to help with that (we don't usually do spoon-feeding, but this is different).

Regarding the other points, I have personally experienced and have also confirmed here on the forums many times that using it (changing all the settings to "Good") increases the battery backup around 15% (10 - 20 %, for example increasing the backup time on my laptop from 3:40 to 4:15). CPU throttling, if that's what you want, is done automatically by the kernel depending upon the demand by the applications. I don't see how 'forcing' it can help.

For example, I was once installing Nero 7 suite on an Asus netbook running Windows 7 Home while travelling. It took around 2 hrs. and still was in progress when I finally cancelled it. When I reached the office to where I was going, I connected it to AC power source, and restarted the installation from start. Finished in less than 18 minutes!! Now that's what a 'forced' throttling or any kind of too aggressive power saving does to you. I can't think who can live with that.

On the other hand, if you are doing nothing but a simple text editing, the Linux kernel (provided you have suitable drivers, especially graphics) will throttle it down to just the level that I guess the Windows 7 'tool' had done in the above case.

Regarding 'Grub Customization', feel free to start a new thread here at Ubuntu Forums if you haven't already. Just make sure to mention 'Mint' so people know what they are dealing with. These are things what we have this "Other OS" section for.

Not trying to compel you to try something, just sharing some experience I have and letting you know of the options we can make available if you want.


Thanks a tone for your reply

Actually, I searched for good tool for throttling the CPU frequency, this what I was after. I tried the "CPU Frequency Scaling Monitor Applet" suggested by "**tgalati4**". It works but suffers a bug which makes all the system input channels freeze if you click on the icon more than once without changing the options in the menu. An example of this is when you try to click on the icon to show the menu to make a change in the settings, then accidentally click somewhere else close to the option, which consequently will lead the menu to disappear. In this you have not made any change in the option when you clicked on the menu last time, and if you do not wait several minutes before clicking on the icon again, the system will freeze. Therefore, I am a little bit careful with it.

I tried the tools you suggested, and as I mentioned , they help in managing the processes of the CPU instead of throttling the frequency. That's why I am still using the "CPU Frequency Scaling Monitor Applet", as I did not find any effective alternative (so far). I use throttling in doing my low level computing, which is the kind of use I do mostly in Linux. I use Windows for the heavy stuff, such as Mechanical CAD, as SolidWorks and AutoCAD do not work on Linux basically. When I do anything related to copying files, installation processes or anything that is preferred to be accomplished in the shortest time possible, I cancel the throttle. However, CPU throttling does work with me for web browsing and office documents work. I use the** *PowerSave*** option in the applet, and does make an important difference compared to using the laptop with Linux, and with nothing installed to manage the power consumption. Nevertheless, this option and the other options of the applet do not work as efficient as the Windows tool does. In Linux I can use the laptop for approximately 2:30-3:00 hours with nothing installed, and almost the same for Windows with the power option "**Balanced**". When I apply the "**Power Save**" option in Windows, the laptop runs up to 4:30-5:00 hours, while it works for almost 4:00 hours with the "**PowerSave**" option selected in Linux.

Due to time constraints currently, I will try to discover the tools you presented more later. Thanks again for you help. Regarding the wireless issue, I'll try to find more about later, but so far, I did not find any effective tool that can do the job. I posted a thread about the Grub problem in LinuxForums, and I think that there is a bug actually in Grub 2.2, as member in the community posted a link related to that. Here is the topic link below:
[http://www.linuxforums.org/forum/ubuntu-linux/202953-grub-text-color-customization.html](http://www.linuxforums.org/forum/ubuntu-linux/202953-grub-text-color-customization.html)


Are there any other suggestions regarding the power management issue ?! OR, should I mark this thread as Solved ?!

---

