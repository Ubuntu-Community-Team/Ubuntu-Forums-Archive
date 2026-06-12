---
title: "How do you change the boot splash screen image for 10.04 Lucid Lynx?"
date: 2010-04-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bxcrx on 2010-04-04
Anyone know how to chance the boot splash image yet?  

In 9.10 I was able to change the image by replacing 

/usr/share/images/xsplash/bg_2560x1600.jpg

with whatever I wanted just as long as I kept the picture name of bg_2560x1600.jpg 

Thanks!

---

### Post by t0cableguy on 2010-04-05
I too want to change the background of the boot splash screen. All I really want to do is replace the purple with a different color.. I am not that fond of purple.

---

### Post by VMC on 2010-04-05
The boot splash is coming from plymouth. Are you asking about that or the login splash?

You need to first go to synaptic and search for 'plymouth', and then add more themes.
From terminal ```
sudo update-alternatives --config default.plymouth
```
Then pay attention to which one has the '*'.

---

### Post by mc4man on 2010-04-05
**Edit:** - Maybe that I'm confusing what you mean, below is for the 'login' screen background, not 'splash'
( to change 'splash' then themes need to b installed to choose from and then run

```
sudo update-alternatives --config default.plymouth
```

Here's how I did it on a tester a week or so ago, still is working fine (*change login background*

[http://ubuntuforums.org/showthread.php?p=9056501#post9056501](http://ubuntuforums.org/showthread.php?p=9056501#post9056501)

(though an update may necessitate redoing..

---

### Post by bxcrx on 2010-04-06
To be clear, I'm looking to change Plymouth's boot image, or color, behind the "Ubuntu...." logo from purple to whatever I would like.

FYI, the logon screen trick did not work for me.  No worries though, I have logon set for automatic.

Thanks!

---

### Post by uonedang on 2010-04-22
Hi bxcrx,

Did you find out how to replace the default boot screen for Lucid 10.04 ?

I am also searching for how to replace the default boot screen (Ubuntu 10.04 ...) 
with a customised screen ... 

If you did, please share  .. what image is to be replaced or what configuration file
to be modified to point to different image, etc .... 


Thanks

Dang

---

### Post by bxcrx on 2010-04-23
nope not yet... Still waiting

---

### Post by Didius Falco on 2010-04-24
This works for me:

Open a Terminal and run this command:

```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```Then logout, and you'll see an Appearance window pop up. Change it to how you prefer it, then close it and login as usual.

When you have logged in after finishing the customizing, run this command to prevent the Appearance window from opening at the GDM screen every time.


```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by Elfy on 2010-04-24
I searched in synaptic for plymouth - found some plymouth themes - installed them than run

```
sudo update-alternatives --config default.plymouth
```

---

### Post by grandtoubab on 2010-04-24
```
gksu -u gdm dbus-launch gnome-appearance-properties
```

and select the background image you want

---

### Post by AntiBodies on 2010-04-24
This (above) worked for me thanks

I think ideally this could be an option in the "Login Screen Settings" under administration.

It makes it look a hell of a lot nicer. there could be options to always sync wallpaper, choose a wallpaper or default etc.

---

### Post by AntiBodies on 2010-04-24
This (above) worked for me thanks

I think ideally this could be an option in the "Login Screen Settings" under administration.

It makes it look a hell of a lot nicer. there could be options to always sync wallpaper, choose a wallpaper or default etc.

---

### Post by 101011010010 on 2010-04-24
Hello, these two tips worked for me.> sudo update-alternatives --config default.plymouth> gksu -u gdm dbus-launch gnome-appearance-properties I changed Login and Splash.Thanks.

---

### Post by cjcj on 2010-04-24
> **Didius Falco said:**
> This works for me:

Open a Terminal and run this command:

```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```Then logout, and you'll see an Appearance window pop up. Change it to how you prefer it, then close it and login as usual.

When you have logged in after finishing the customizing, run this command to prevent the Appearance window from opening at the GDM screen every time.


```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

:) Thanks, this allowed me at last to get rid of the gloomy brown dungeon screen that somehow for me did not get changed when I upgraded to Lucid some while ago. Now all I need to do is work out how to get Plymouth working.

---

### Post by Didius Falco on 2010-04-24
Forestpiskie gave you the good info on changing the boot splash - I was a bit confused about what, exactly you wanted to change.

I also found a good tutorial on making your own Plymouth themes:

[http://brej.org/blog/?p=158](http://brej.org/blog/?p=158)

That's a link to Part 1 - there is a total of 4 parts. Using the information from this guide, I've created my first custom theme.

In combination with the tip I posted above about changing the gdm (log in) screen, and just plain changing the wallpaper on the desktop, I now have the same background from boot to the desktop, and it's easy to change.

I'm still refining my theme, but it beats the heck out of that "Purple Bordello" default theme. ;)

---

### Post by mordak13 on 2010-04-26
> **Didius Falco said:**
> This works for me:

Open a Terminal and run this command:

```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```Then logout, and you'll see an Appearance window pop up. Change it to how you prefer it, then close it and login as usual.

When you have logged in after finishing the customizing, run this command to prevent the Appearance window from opening at the GDM screen every time.


```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

Thanks for this. Somehow, I ended up with that White and Red Orchid as my login wallpaper and didn't want it so this solved my wallpaper woes. :biggrin:

---

### Post by cariboo on 2010-04-26
For those that want an easy way to change gdm background and theme try gdm2setup, the ppa is here:

[https://launchpad.net/~gdm2setup/+archive/gdm2setup](https://launchpad.net/~gdm2setup/+archive/gdm2setup)

---

### Post by mordak13 on 2010-04-26
> **cariboo907 said:**
> For those that want an easy way to change gdm background and theme try gdm2setup, the ppa is here:

[https://launchpad.net/~gdm2setup/+archive/gdm2setup](https://launchpad.net/~gdm2setup/+archive/gdm2setup)

Cool I'll give it a look when I get home later today. Thanks. :biggrin:

---

### Post by Didius Falco on 2010-04-26
> **cariboo907 said:**
> For those that want an easy way to change gdm background and theme try gdm2setup, the ppa is here:

[https://launchpad.net/~gdm2setup/+archive/gdm2setup]("https://launchpad.net/%7Egdm2setup/+archive/gdm2setup")


gdm2setup and my pc didn't get along well. I couldn't actually change the image, and every time I used it two of the "Universal Access" icons would appear in the notification area.

One I could remove easily, the other required: Alt+F2/ gnome-keyboard-properties/uncheck the box that says "Accessibility features can be toggled with keyboard".

Lots of others are using it without problems though, so it's likely a quirk of my own setup...

---

### Post by mordak13 on 2010-04-26
> **Didius Falco said:**
> gdm2setup and my pc didn't get along well. I couldn't actually change the image, and every time I used it two of the "Universal Access" icons would appear in the notification area.

One I could remove easily, the other required: Alt+F2/ gnome-keyboard-properties/uncheck the box that says "Accessibility features can be toggled with keyboard".

Lots of others are using it without problems though, so it's likely a quirk of my own setup...I had the same issue with the commands I used above. I got rid of one but the other persisted. Thanks for this info to get rid of the other one. I haven't got to play with gdm2setup yet.

---

### Post by Didius Falco on 2010-04-26
My pleasure, Mordak13!

---

### Post by chek2fire on 2010-04-26
I still have the old grub because my distro is from third upgrade. Do we have a how to for the old grub?

---

### Post by Didius Falco on 2010-04-26
I'm still using legacy grub (Because grub 2 is from SATAN!!! :twisted:)  and I'm using the above with no problems.

---

### Post by bxcrx on 2010-04-27
Are these commands suppose to change this (below)to any image I want?

[img]http://common.ziffdavisinternet.com/util_get_image/25/0,1425,i=258228,00.jpg[/img]

If it does then I've had no luck with any of the suggestions so far.

---

### Post by frogotronic on 2010-04-27
Is there a GUI for this?

- CH    :guitar:

---

