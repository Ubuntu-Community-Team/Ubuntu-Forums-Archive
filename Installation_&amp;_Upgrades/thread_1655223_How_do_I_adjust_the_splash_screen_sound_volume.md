---
title: "How do I adjust the splash screen sound volume"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by Pudellvr on 2010-12-29
I have recently installed ubuntu on a Dell Inspiron 8500. It works well but the startup volume on the ubuntu splash screen is extremely loud. How do I adjust this. System volume does not seem to help.

---

### Post by Pudellvr on 2010-12-30
could someone please help me with this?

---

### Post by ottosykora on 2010-12-30
I would also be interested in this, since the laud sound on start up is problematic in rooms where more people do work.

---

### Post by j388m on 2010-12-30
I would also like to know this answer.

---

### Post by matt_symes on 2010-12-30
Hi

I don't know if this will work as it's taken from this post and it's a bit old.

[http://ubuntuforums.org/showthread.php?t=1357730](http://ubuntuforums.org/showthread.php?t=1357730)

System->Preferences->Sound : Adjust the Alert Volume and reboot to hear.

I hope it works.

Kind regards

---

### Post by WthIteh on 2010-12-30
Usually I don't hear loud sound on start-up. I didn't check it exactly but it seems that the sound preference will remain constant (remembered) after boot.
So simply mute or turn down your sound volume before shutting down and then the start-up sound will go away.

---

### Post by holiday on 2010-12-30
Is there a sound preferences option somewhere - like Windows has - where I can assign sounds (or disable sounds) for a particular event. I like most of the sounds, but the startup sound is startling and sometimes embarrassing.

I know I can disable all sounds, and I can mute before shutdown, but neither solution is ideal. 

I think I remember this option being a feature of Ubuntu's desktop, but I don't see it now.

---

### Post by matt_symes on 2010-12-30
Hi

If you want to turn off the logon screen sound you can do that from

System->Administration->Logon screen and uncheck Play log-in sound.

You will then have no log in sound at all. My other post was a potential solution to make it quieter.

Kind regards

---

### Post by holiday on 2010-12-30
> **matt_symes said:**
> Hi

If you want to turn off the logon screen sound you can do that from

System->Administration->Logon screen and uncheck Play log-in sound.

You will then have no log in sound at all. My other post was a potential solution to make it quieter.

Kind regards


Thank you.

---

### Post by Pudellvr on 2011-01-03
None of these solutions work. The startup drum beat and oooohhhs are deafening. Sound is moderate to low playing on the system. Alerts turned off.

---

### Post by matt_symes on 2011-01-03
Hi

Did you try..

```
System->Administration->Logon screen and uncheck Play log-in sound
```

To switch the logon sound off?

Kind regards

---

### Post by matt_symes on 2011-01-03
Hi

There is a way to make the login sound queiter (not the drums, the sound after your have enetred you logon details).

Go to System->Preferences->Gnome logon sound.

The command will contain a string like

```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```

This can be made quieter by adding --volume="-10" or another value.

You can test this. Open a terminal and type

```
matthew@matthew-laptop:~$ /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login" --volume="-10"
```

Have a play with the -10 value until you find a value you are happy with and then add that value as a string in System->Preferences->Gnome logon sound.

Half way there. Just the drums to make quieter now.

Kind regards

---

### Post by Pudellvr on 2011-01-03
Yes, I did. It still played on restart.

---

### Post by matt_symes on 2011-01-03
Hi

Alright. If you can't disable the drums sound when you log in from the System->Administration->login screen, try this. Open a terminal and type

```
sudo chmod 000 /usr/share/sounds/ubuntu/stereo/system-ready.ogg
```

Enter your password. You will not see it echoed to the screen. This is normal. Reboot and try again.

Hopefully that will disable the drums sound and you can now disable or quieten the other logon sound. (from post 12)

Kind regards

---

### Post by Pudellvr on 2011-01-03
> **matt_symes said:**
> 

You can test this. Open a terminal and type

```
matthew@matthew-laptop:~$ /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login" --volume="-10"
```Have a play with the -10 value until you find a value you are happy with and then add that value as a string in System->Preferences->Gnome logon sound.

Half way there. Just the drums to make quieter now.

Kind regards

recd the following error "Failed to play sound: Sound disabled"

I do appreciate your help.

---

### Post by matt_symes on 2011-01-03
Hi

> recd the following error "Failed to play sound: Sound disabled"

Blimy. What is going on with your PC ? :confused: When are you getting that error message? When you try to play it in the terminal ?

Are you still getting the loud drum sound when the gdm logon screen is displayed? Are you still getting the sound when it is loading gnome?

Please post the output of 

```
ls -l /usr/share/sounds/ubuntu/stereo
``` That is a small L (for the drum sound)

also please post the output of 

system->preferences->Startup applications->Gnome login sound->edit->command

Kind regards

---

### Post by Pudellvr on 2011-01-03
I assume that it means I have the login sound disabled. I promise you it is not ticked but when I log in I keep earphones plugged into the computer. I am afraid that it is loud enough to pop the speakers. Both the drum beat and the ahhhs! I have to go to work now and will be aftk until tonight. My other dell laptop that I loaded ubuntu onto a lattitude 1404 does not have this problem. I actually reloaded this one twice due to this problem.

---

### Post by matt_symes on 2011-01-03
Hi

_Exactly_ what have you tried so far?

Give me the steps you have taken to disable or quieten the sounds.

Have you tried all the solutions i have presented? Unticking that box on the logon screen was only one solution i proffered.

Kind regards

---

### Post by Pudellvr on 2011-01-05
Sorry it has taken me so long to answer back. Our school semester started back so my daughter is 
using the laptop all morning. I work every evening. I will try your newest fix soon and post
results. This is what I have tried so far.:popcorn:

System->Administration->Logon screen and uncheck Play log-in sound
    Did this no change in either sound

/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
       this had no effect

matthew@matthew-laptop:~$ /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login" --volume="-10"
     same with this--it was a duplicate right?

sudo chmod 000 /usr/share/sounds/ubuntu/stereo/system-ready.ogg
      Received this error "Failed to play sound: Sound disabled"

---

### Post by matt_symes on 2011-01-05
Hi

> /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

this had no effect

No. Try (in the terminal)

```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login" --volume="-20"
```

Notice the volume switch. Play with the value of --volume="-20"
in the terminal until you get a comfortable volume. Make sure it's a negative number

When you are comfortable with the volume go to

System->Preferences->Startup applications. Scroll down to Gnome logon sound. 

Click the EDIT button on the right hand side

Copy and paste the string

```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login" --volume="-20"
```

with your preferred volume into the command edit box and click save. That will change the volume of the Gnome logon sound. You can turn that off altogether if you want by unchecking the tick box next to Gnome Logon sound.

To switch off the drums open a terminal and type

```
sudo chmod 000 /usr/share/sounds/ubuntu/stereo/system-ready.ogg
```

and enter your password. You will need to do this if....

System->administration->Login screen: Uncheck play logon sound.

...failed.

I don't know how to make the drums quieter only how to turn them off. 

Kind regards

---

### Post by matt_symes on 2011-01-05
Hi

Please see screen shots. Post below. Internet connection went *hick* ;)

Kind regards

---

### Post by matt_symes on 2011-01-05
Hi

Please see screen shots. Hopefully they will make it clearer.

If that does not work then i am a bit stumped, as it works on all my machine running Ubuntu.

Kind regards

---

### Post by matt_symes on 2011-01-05
Hi

...and here is another screen shot.

Kind regards

---

### Post by Pudellvr on 2011-01-05
[IMG]file:///home/tricia/Desktop/Link%20to%20error%20msg%201.png[/IMG][IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG][IMG]http://i716.photobucket.com/albums/ww162/pudellvr/linux/Screenshot.png[/IMG]

---

### Post by matt_symes on 2011-01-05
Hi

Oh dogs dinner!!!!

```
usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login" --volume="-20"
```

It should be **/**usr/.....

Look here. Notice the initial / to make the path absolute.

```
**/**usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login" --volume="-20"
```

My **/** key is sticking sometimes. Must clean my keyboard.

Try that.

I have edited my other post.

Kind regards

---

### Post by Stubbs3 on 2011-01-05
I have the same exact issue only im going through 4 channels of a 50 Watt amplifier!  Startles me every time!
I have done 3 complete ubuntu reinstalls (for other reasons). 2 of 9.04 and 1 of 10.04. In my case Ive noticed that it would only startup at max volume at login (drums and ahhhh) after installing **pulse audio equalizer**. System volume would normally be at low during exit and at desktop screen after startup.
Not sure of any of this is the same for you. I'm still looking for a answer.
Ive tried [matt_symes]("http://www.uluga.ubuntuforums.org/member.php?u=1067998") but it did not work for me.
Thanks though matt. :KS
     Code:
     **/**usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login" --volume="-20"

---

### Post by matt_symes on 2011-01-06
Hi

> In my case Ive noticed that it would only startup at max volume at login (drums and ahhhh) after installing pulse audio equalizer

That's really odd. I also have pulse audio equaliser installed but it still works for me. Did you try turning both sounds off as opposed to just down?

It must be some setting somewhere though.

Kind regards

---

### Post by Stubbs3 on 2011-02-08
Tried it again matt and it worked! For 2 of my PC's
Thanks again, Stubbs:guitar:

---

### Post by towheedm on 2011-02-08
And to replace your login sound without replacing the desktop-login.ogg file, replace --id="desktop-login" with:

--file="/dir/newloginsound.ogg|oga|wav"

Note that the path must be an absolute path, ie: /home/user/sound/loginsound, not ~/sound/loginsound.

---

