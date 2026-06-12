---
title: "[SOLVED] Ubuntu 7.10 install problem"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by archer6 on 2008-04-07
After installing Ubuntu 7.10 on my R51e ThinkPad I get this: 

When I boot up after grub loads I get a message saying: 

[5.45398] MP-BIOS Bug: 8254 timer not connected to IO-APIC
[11.13031818] PCI cannot allocate resource to region 7 of the bridge
[11.33345455] PCI cannot allocate resource to region 8 of the bridge

I may be off on the numbers as this screen goes by so fast that it's hard to copy the numbers which also seem to change each time I boot it. Is there a way to stop this screen long enough to get the numbers accurately, or is that not needed?

Then it proceeds to hang with a black screen for 2 to 5 minutes, then the Ubuntu screen appears asking for my username, then password, then it boots into the program. At that point I can navigate, launch programs such as open office and use it. 

Any or all suggestions very welcome. Thanks!

---

### Post by Partyboi2 on 2008-04-07
You could try a few things
1. Try adding noapic as a boot option.
When your system boots and you see grub loading...press ESC to get to grub menu screen then highlight the kernel you are booting and press "e" then highlight the line starting with "Kernel" and press "e" again then at the end of the line add ```
noapic
``` then press "b" to boot. If this works you can make it permenant
 by adjusting your grub menu.lst file.

2.Turn off IOAPIC
If you are able to you can try turning off IOAPIC in your bios and see if that works. Some motherboards don't allow you to do this though.

3. Update bios
You could try updating your bios to a later version.

---

### Post by archer6 on 2008-04-08
> **Partyboi2 said:**
> You could try a few things

Thank you very much for the detailed suggestions. I will be trying these later today and report back. 

Your assitance is greatly appreciated

Cheers!

---

### Post by archer6 on 2008-04-09
> **Partyboi2 said:**
> You could try a few things
1. Try adding noapic as a boot option.
When your system boots and you see grub loading...press ESC to get to grub menu screen then highlight the kernel you are booting and press "e" then highlight the line starting with "Kernel" and press "e" again then at the end of the line add ```
noapic
``` then press "b" to boot. ..

Ok, I followed the instructions above exactly, after entering noapic to the end of the line, and then presssing "b" to boot. Nothing Happens. 

I tried this a couple of times to insure that I had not made a mistake or mistyped something but got the same result. Everything goes well until the very end, when pressing b nothing happens.

Any suggestions? 

Also if and when I get this line corrected, if it does fix it, below you say "make it permenant by adjusting your grub menu.lst file". 

Please explain how to do this.

Thanks!


> **Partyboi2 said:**
> If this works you can make it permenant  by adjusting your grub menu.lst file.


2.Turn off IOAPIC
If you are able to you can try turning off IOAPIC in your bios and see if that works. Some motherboards don't allow you to do this though.

3. Update bios
You could try updating your bios to a later version.

---

### Post by archer6 on 2008-04-09
> **archer6 said:**
> Ok, I followed the instructions above exactly, after entering noapic to the end of the line, and then presssing "b" to boot. Nothing Happens. 

Just for clarification and in case it helps, When I installed Ubuntu on my ThinkPad R51e, I did so as a complete single OS installation, _not a dual boot_ with Windows XP. XP is gone.

 The only OS on the computer now is Ubuntu 7.10.

Thank You

---

### Post by Partyboi2 on 2008-04-09
> Ok, I followed the instructions above exactly, after entering noapic to the end of the line, and then presssing "b" to boot. Nothing Happens.make sure you press "enter" before you press "b" 
To make it permanent you need to open up the grub.menu.lst file. In a terminal (Applications>Accessories>Terminal)
```
gksudo gedit /boot/grub/menu.lst
``` then look for this section:
> ## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
[COLOR=Red]# kopt=root=UUID=c61e113a-1e75-40cc-8051-bcceeb33acff ro quiet splash[/COLOR] and at the end of the line starting with [COLOR=Red]# kopt=root[/COLOR] you would add noapic so it would look something like this:
```
# kopt=root=UUID=c61e113a-1e75-40cc-8051-bcceeb33acff ro quiet splash noapic

``` then save the file
and in the teminal update grub
```
sudo update-grub
```

---

### Post by archer6 on 2008-04-10
> **Partyboi2 said:**
> make sure you press "enter" before you press "b" 

Here's the latest. After carefully following the intructions, and pressing "enter" before pressing "b" did indeed take it into the bootup mode. However the same three lines appeared as I originally reported, and as listed below.

[5.45398] MP-BIOS Bug: 8254 timer not connected to IO-APIC
[11.13031818] PCI cannot allocate resource to region 7 of the bridge
[11.33345455] PCI cannot allocate resource to region 8 of the bridge

After which the screen goes blank, just as though it was continuing the boot process. I can see HD disk activity due to the blinking light. Prior to this most recent set of intructions it would stay black with the HD light blinking, then eventually bootup into a useable destkop within 2 to 5 minutes. When using the most recent set of instructions you were kind enough to post, after seeing the three lines above, the display goes black, and activity is seen on the HD indicator light, then approx 8 to 10 minutes later I'm greeted by the Ubuntu screen with the field requesting the Username:, then after entering that, the field for password, from which it boots quicky to a normal, stable desktop. 

At that point everything (with the exception of wifi) works normally. I can launch and use Open Office, games, etc. 

The issue with the WiFi is also something that must require nothing more than a simply resolution. 
When I click on the network connection icon on the top of the display a drop down menu appears which does indeed list my Wi-Fi provider (tmobile) and in the progress bar area it has the longest bar, which is about 50% across towards full power. Just in case it matters here is the list I see in the drop down menu.

2wire126
2WIRE189
2WIRE222
2WIRE254
2WIRE420
2WIRE504
2WIRE840
7235 0604
7444 5544
Ace Cash Express
linksys
tmobile  (my provider & the connection I want)

However when I click on the radio button to the left, to choose it, the list goes away, replaced by somewhat slowy spinning blue dash rotating clockwise between two dots, in the notification area above. 

It's as thought it's trying to connect but cannot. Eventually (about 4 minutes) the spinning stops and if I hover my mouse over it a box apprears saying "attemtping to joint the wireless network "tmobile" .

At this point there is a small red box with an X below the dual monitor network icon and it says No network connection. When I click on it, the list of available networks is gone. Replaced by a label:

Wireless Networks
------------------------------------------
Connect to other wireless network.....
Creat new wireless network.....
Manual configuration.............


So there is the most current report as to what's happening (or not) with my Ubuntu 7.10 install.

Again I would like to thank you for your continued support, especially since I'm a beginner, have great windows skills, but nothing in Linux.

Therefore your time, instrucion, and attention to detail is greatly appreciated. I know that once up and running I will then have  a platform to learn from and it's very exciting to take on something from the ground up. 

Cheers!

---

### Post by archer6 on 2008-04-10
Here is the latest.

I included a space before entering the word noapic. This took care of it. Now when I boot up that line no longer appears. 
So we are making progress. 

That said, now what remains during the boot process is the appearance of the two lines:

[11.13031818] PCI cannot allocate resource to region 7 of the bridge
[11.33345455] PCI cannot allocate resource to region 8 of the bridge

After these two are displayed, then again the screen goes black and the wait for it to finally boot up remains about 5 minutes, sometimes longer to the point where the display goes to sleep. The minute I notice this, I hit the FN key to wake it up and the desktop appears at the very same time, requesting the username, password and then we are up and running fine, yet less the ability to connect with WiFi as I mentioned earlier.

Please Advise.....Thanks 
Oh, and for point of refernece, once I am at the destkop and using Open Office, again it  is working just fine.
Then upon deciding to shut down. I carefully watched that process and everything acts properly when using the shut down command. 

Therefore once we can sort out the boot up and time delay, get the WiFi to connect, stay connected and function, I will be good to go.

Thanks!

---

### Post by archer6 on 2008-04-10
> **archer6 said:**
> Here is the latest.

I included a space before entering the word noapic. This took care of it. Now when I boot up that line no longer appears. 
So we are making progress. 

That said, now what remains during the boot process is the appearance of the two lines:

[11.13031818] PCI cannot allocate resource to region 7 of the bridge
[11.33345455] PCI cannot allocate resource to region 8 of the bridge

After these two are displayed, then again the screen goes black and the wait for it to finally boot up remains about 5 minutes, sometimes longer to the point where the display goes to sleep. The minute I notice this, I hit the FN key to wake it up and the desktop appears at the very same time, requesting the username, password and then we are up and running fine, yet less the ability to connect with WiFi as I mentioned earlier.

Please Advise.....Thanks 
Oh, and for point of refernece, once I am at the destkop and using Open Office, again it  is working just fine.
Then upon deciding to shut down. I carefully watched that process and everything acts properly when using the shut down command. 

Therefore once we can sort out the boot up and time delay, get the WiFi to connect, stay connected and function, I will be good to go.

Thanks!

Updated Again:  Here's the latest.

I removed the boot splash screen so I could watch what was happening. Although I didn't actually see a splash screen, just a plain black screen and a lot of waiting. 

Here is an event list (highlights only) from cold boot up.

Press power button
Watch as grub loads
Watch as these two lines still appear:
[11.13031818] PCI cannot allocate resource to region 7 of the bridge
[11.33345455] PCI cannot allocate resource to region 8 of the bridge
Then watch as many text lines scroll by until it finally stops / hangs at:
**Starting Common Unix Printing System cuspd** where it remains hung for two minutes.
Then the rest of the files load and the username screen appears, then password then desktop.

Total time now down to approx 5 minutes. This was after two test cycles.

Now an even more bizarre experience. I booted it for the fourth time to double check the time from first press of the power button to the appearance of the desktop, and this time, the screen was again blank & black instead of allowing me to watch what was happening. This time it takes 8 minutes to get to the desktop. Very challenging and a bit frustrating I might ad. The irregular behavior is troubling, considering I did save the changes. 

Furthermore this time when it did come up after 8 minutes I used Esc to check the line, which now at the end reads:  ro quiet noapic quiet splash

What happened? It's this a case of user error.....:)   I can be quite good at that......:KS

Signed: 
Dazed.....confused.....Yet Very Determined with a Positive Attitude....:)

---

### Post by Partyboi2 on 2008-04-10
check your /etc/usplash.conf file and make sure that it matches what ever your screen supports. As this can cause a slow boot to the login screen. So for example if your screen resolution is 1280x1024 it would look like this:
> # Usplash configuration file
xres=1280
yres=1024 or 1024x768 reolution  would look like
> # Usplash configuration file
xres=1024                                                                                                                    
yres=768 If you need to change these numbers to match your correct screen resolution you will need to update the theme after saving the changes, by typing in the terminal
```
sudo update-usplash-theme usplash-theme-ubuntu
```

> Furthermore this time when it did come up after 8 minutes I used Esc to check the line, which now at the end reads: ro quiet noapic quiet splash you only need the word quiet once.

---

### Post by archer6 on 2008-04-10
> **Partyboi2 said:**
> check your /etc/usplash.conf file and make sure that it matches what ever your screen supports. As this can cause a slow boot to the login screen. So for example if your screen resolution is 1280x1024 it would look like this:
 or 1024x768 reolution  would look like
 If you need to change these numbers to match your correct screen resolution you will need to update the theme after saving the changes, by typing in the terminal
```
sudo update-usplash-theme usplash-theme-ubuntu
```

 you only need the word quiet once.

How do I find the /etc/usplash.conf file? 

My resolution is 1024x768 on a 14" display.

Is that accessed via the terminal window? 
And if so, would you be so kind to list exactly how. I'm sure once I get the basics of how to work in the terminal window this will be much easier. 

Thanks

---

### Post by Partyboi2 on 2008-04-10
Sorry I forgot to give the command. Open a terminal (Applications>Accessories>Terminal) and open the file by typing
```
gksudo gedit /etc/usplash.conf 
``` (gksudo gives you admin rights to change the file and gedit is a gnome text editor) then make sure the contents of the file looks like this:
> # Usplash configuration file
xres=1024                                                                                                                    
yres=768                       If you need to change it then after you have saved the changes back in the terminal type:
```
sudo update-usplash-theme usplash-theme-ubuntu
```then reboot and see if it is faster.

---

### Post by archer6 on 2008-04-10
Thanks!

Just a quick question while I wait for it to boot up.

I shut down properly about 2 hours ago, and put my laptop in it's case. Just now when pulling it out of the case it was very warm as though it had stayed on while in the case. 

However there was no sign of that, no light, no other indicators. Yet instead of being cold it was very warm? 

Ideas? 

Thanks again, I'm getting a great education here because of your help, courtesy and professionalism. Your time is greatly appreciated!

---

### Post by Partyboi2 on 2008-04-10
> **archer6 said:**
> Thanks!

Just a quick question while I wait for it to boot up.

I shut down properly about 2 hours ago, and put my laptop in it's case. Just now when pulling it out of the case it was very warm as though it had stayed on while in the case. 

However there was no sign of that, no light, no other indicators. Yet instead of being cold it was very warm? 

Ideas? 

Thanks again, I'm getting a great education here because of your help, courtesy and professionalism. Your time is greatly appreciated!
The only thing I can think of is that when you were using the laptop a few hours ago it was getting a good work out (so to speak) and when you put it back in the case the case didn't allow the heat to escape. Not something that I am really to sure about.

---

### Post by Victormd on 2008-04-10
> **archer6 said:**
> 
I shut down properly about 2 hours ago, and put my laptop in it's case. Just now when pulling it out of the case it was very warm as though it had stayed on while in the case. 

However there was no sign of that, no light, no other indicators. Yet instead of being cold it was very warm? 

Ideas? 

Thanks again, I'm getting a great education here because of your help, courtesy and professionalism. Your time is greatly appreciated!

Well, it's hard to say because, as you said, there was no indication that the laptop was on or on standby.  Furthermore, when you turned it on, did it cycle through BIOS and GRUB and the whole booting process? If so, then it's safe to say that it was fully powered down (still doesn't explain the high temp.), otherwise, it might have been in standby without you knowing.

---

### Post by archer6 on 2008-04-10
Question: Copied (below) and pasted from earlier instructions: (as I did have to correct the resolution)

If you need to change these numbers to match your correct screen resolution you will need to update the theme after saving the changes, by typing in the terminal

Code:
sudo update-usplash-theme usplash-theme-ubuntu

After I perform the command above do I press "enter" or ? 





Yes it was indeed fully powered down. Just warm as you mentioned most probably from the workout earlier, as I was using it non-stop for a couple of hours while making the adjustments.

Now I'm waiting for it to boot up again. to remove one of the quiets' ( I had two, so much correct this.)

I did indeed have to adjust for the correct resolution as it was defaulted to 1280 x 1024 instead of the native 1024 x 768 so I made the adjustement

---

### Post by Partyboi2 on 2008-04-10
Yes after you have typed in the terminal window
>  sudo update-usplash-theme usplash-theme-ubuntu you need to press enter and you will see it update.
But make sure you have closed the /etc/usplash.conf file first.

---

### Post by archer6 on 2008-04-10
> **Partyboi2 said:**
> Yes after you have typed in the terminal window
 you need to press enter and you will see it update.
But make sure you have closed the /etc/usplash.conf file first.

Ok, that seemed to go well. I double checked to see that the change I made to 1024 x 768 saved properly and it did. 

Then I was ready to shut down (instead of chosing restart) the Ubuntu Logo was back, everything looked good as it shut down, and it shut down very smoothly and quickly. 

Waited 1 minute, then pressed the power button to boot up. Saw the grub loader, then it said Starting up..... great so far, then saw the two lines appear:

[11.13031818] PCI cannot allocate resource to region 7 of the bridge
[11.33345455] PCI cannot allocate resource to region 8 of the bridge

Then a black screen, hard drive light blinking as normal prior to boot, and it's been about 5 minutes and the display is still blank / black, and waiting for it to display screen that askes for username, then password.

Could the current delay be caused by those two remaining lines above referencing PCI cannot allocate? 

We are making progress and I feel as though we might be very close to our goal.

Ideas?

Thanks

---

### Post by archer6 on 2008-04-10
Since it was still black, I tapped the FN key and it came to life? 

I experienced this once earlier today.

Thoughts?

---

### Post by archer6 on 2008-04-10
Update:

4th complete shutdown and reboot, took 8  minutes

I've double checked most everything I can think of that I did earlier. Perhaps I'm missing something?

---

### Post by archer6 on 2008-04-10
Shutdown part of routine seems to be perfect. 

As soon as I choose shut down, the full size Ubuntu splash screen appears clearly, and moments later it shuts down completely. This is a relatively new development since the changes I made based on the instructions here. 

Now it seems like if we can get it to boot up in a resonable period of time, we've got it. 

Cheers

---

### Post by Partyboi2 on 2008-04-10
I was just reading earlier that a few people have had problem with slow boot with the thinkpad R51e and they reduce the time by adding ec_intr=0 as a boot option. Maybe try booting with this to see if it reduces the boot time. To add it you need to do the same as you did when you added noapic. So when you boot and get to where it is saying it is loading grub press esc to enter the grub menu then highlight the kernel you nornally boot into and press "e" then highlight the line starting with kernel and press "e" again and at the end of the line add 
```
ec_intr=0
``` like you did when you added noapic then press enter and then "b" to boot. See if the time is reduced  and let me know. You may need to remove noapic from the grub menu.lst to see if this works. So try first by adding ec_intr=0 to the boot options if it does not work then try removing noapic from grub menu.lst and then adding ec_intr=0 to the boot options.

---

### Post by archer6 on 2008-04-10
> **Partyboi2 said:**
> I was just reading earlier that a few people have had problem with slow boot with the thinkpad R51e and they reduce the time by adding ec_intr=0 as a boot option. Maybe try booting with this to see if it reduces the boot time. To add it you need to do the same as you did when you added noapic. So when you boot and get to where it is saying it is loading grub press esc to enter the grub menu then highlight the kernel you nornally boot into and press "e" then highlight the line starting with kernel and press "e" again and at the end of the line add 
```
ec_intr=0
``` like you did when you added noapic then press enter and then "b" to boot. See if the time is reduced  and let me know. You may need to remove noapic from the grub menu.lst to see if this works. So try first by adding ec_intr=0 to the boot options if it does not work then try removing noapic from grub menu.lst and then adding ec_intr=0 to the boot options.


Excellent, a fresh Idea! 

I feel confident that I am now familiar enough to get this done. One small question, should it be added to the end of the same line with noapic? 

Thanks

---

### Post by archer6 on 2008-04-10
Oops.....sorry, I read too fast, as your instructions were perfect and I am to add it to the end of the line.

Also did you notice my earlier comment about the wifi issue. It trys to connect, sees my tmobile account ok, but does not connect and stay connected?

---

### Post by Partyboi2 on 2008-04-10
You might want to consider opening up a new thread [here]("http://ubuntuforums.org/forumdisplay.php?f=136") for your wireless problem as I have limited knowledge when it comes to wifi setup.

---

### Post by archer6 on 2008-04-10
> **Partyboi2 said:**
> You might want to consider opening up a new thread [here]("http://ubuntuforums.org/forumdisplay.php?f=136") for your wireless problem as I have limited knowledge when it comes to wifi setup.


Great Suggestion!

I am continuing to try different combinations to see if I can overcome this long boot time. As you suggested it is indeed unique to the R51e......

I would be happy if I could get the boot time down around 3 minutes. I'm not looking for perfection, just something that I can live with.

Thanks for all your help and I will check in with you tomorrow.

Cheers!.....:)

---

### Post by archer6 on 2008-04-11
**_[SIZE="3"]Thank You Partyboi2 ![/SIZE]_**

We Have Victory!

Your diligent efforts to educate me, by contributing your valuable time, efforts, patience and expertise have provided an excellent foundation in my first days witih Linux as a complete novice. 

The challenges I have faced during this somewhat problem filled installation, have from my beginners perspective, been rather daunting. Without your assistance I would still be struggling. 

Thanks to you, I now have my ThinkPad R51e up and running so that I may now use it on a daily basis as a great point of entry into the world of Linux. 

As you will remember I began with the challenge of a very slow and unstable boot up time of 8 minutes (or more) as well as a few other issues, which I have learned is somewhat the norm for this particular R51e model ThinkPad. 

The great news is now that time has been reduced to a very acceptable 2 minutes, 5 seconds. Not only that, it's very stable, as I have repeatedly tested it from cold boot, over and over. 

Tomorrow is a new day, and I'm thrilled to have the peace of mind knowing that I now have a reliable, stable install of Ubuntu 7.10 to work with going forward.

I am eager to experience a very interesting journey and education on the Linux OS Distro known as Ubuntu  7.10

Thanks,
Archer 6

---

### Post by Partyboi2 on 2008-04-11
Happy to help, hope you get your wireless working soon :)

---

