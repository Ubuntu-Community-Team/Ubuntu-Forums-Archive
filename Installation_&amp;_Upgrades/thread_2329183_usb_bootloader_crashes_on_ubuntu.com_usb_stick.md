---
title: "usb bootloader crashes on ubuntu.com usb stick"
date: 2016-06-28
forum: Installation &amp; Upgrades
---

### Post by geogur on 2016-06-28
i cant use your usb 16.04 its flawed , i take out a old ubuntu 12.04 and it installs and finds a network ?

---

### Post by gordintoronto on 2016-06-29
How is 16.04 flawed? If you provide details, perhaps someone can help you.

---

### Post by RobGoss on 2016-06-29
> **geogur said:**
> i cant use your usb 16.04 its flawed , i take out a old ubuntu 12.04 and it installs and finds a network ?


We are not really sure what your question is you'll have to be more detailed with your question

---

### Post by geogur on 2016-06-30
Okay im using Bodi 12 my Ubuntu 16 usb gets to the 5th step of the install and crashes 
I was running 14 but lost it tryimg to install , (backed up no worries) 

Im going to start hear and make my way to 16 ,im trying a dual boot to load ubuntu 16

---

### Post by geogur on 2016-07-02
so nothing is working this is going to be fun so i can run it live but will not install , crashes evey time .

---

### Post by sudodus on 2016-07-02
Please tell us as much as possible about your computer, at least

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

and the output of the following commands (when you run a live session booted from the Ubuntu USB drive)

```
sudo parted -ls
sudo lsblk -fm
df
```

Then we have a better chance to help you :-)

---

### Post by geogur on 2016-07-05
Antec 900 case 
intell media board 
intell dual core chip 
8 gb matched ram (asus)
seagate hd 1 tb new (yesterday)
asus silent cooling vidio card (dont know model number)

i took out my wd 1tb hd (8 years old) thinking it was defective but the new seagate drive get faulty drive cautions too

---

### Post by geogur on 2016-07-05
if i download or use the ubuntu bought usb it crashes at the same spot 

can i install the usb using a xterm ? 

if so will sudo help

---

### Post by geogur on 2016-07-05
i did run the code but cant seam to copy the xterm into this forum , im dumb
and i am using the usb live so i have 16.04 lts just no install

---

### Post by sudodus on 2016-07-06
> **geogur said:**
> Antec 900 case 
intell media board 
intell dual core chip 
8 gb matched ram (asus)
seagate hd 1 tb new (yesterday)
asus silent cooling vidio card (dont know model number)

i took out my wd 1tb hd (8 years old) thinking it was defective but the new seagate drive get faulty drive cautions too

It is possible, even likely, that you have problems with the video card. Please try to find out what chip there is on that card!

Try with the following command in a terminal window

```
hardinfo
```

Select *PCI devices -- VGA compatible controller*

and tell us the 'Name' in the device information list.

If hardinfo is not installed (in your live system booted from the USB drive), please install it temporarily by

```
sudo apt-get install hardinfo
```

As a start, you can try to use the boot option **nomodeset**. See this link and links from it for instructions how to add/change boot options

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

---

### Post by geogur on 2016-07-06
unable to find hardinfo , even if i try to install it 
i will dissasemble my case and take out the vidio card if needed

why the vidio card? , do i need to replace or can i work around the problem

---

### Post by sudodus on 2016-07-06
You might be able to work around it with nomodeset or some other boot option, and maybe in the next step with a proprietary graphics driver. But it is very difficult to help, when I don't know exactly what hardware it is. I can only guess; there might be other problems.

-o-

But if you have the time and patience, I have it too (as well as many other people at our Ubuntu Forums who might chip in and help), and gradually we can find out more about your computer and your problems. With enough time and effort I think we can solve your problems.

Is your computer booting and running with good graphics from the Ubuntu USB drive?

Which version of Ubuntu works for you? I'm asking about 'running live' or 'Try Ubuntu' that is booting from the Ubuntu USB drive. (I am not asking about installing now, let us look at that problem later.) See also the following link,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by geogur on 2016-07-06
okay i set Navida and intel pro drivers . instead of default .
Now i install but hang on the seaching for time from a network time server box 
i can open up a little xterm below and see the activity but hangs here and time is not set but i www. access

---

### Post by sudodus on 2016-07-07
It seems your computer can boot and run from a USB boot drive. When running like that, please run the following command in a terminal window (xterm or similar).

```
sudo bash -c 'lshw -sanitize > lshw.txt'
```

In a live system you will not be asked for a password (but you would, if you run this command in an installed system.)

Click on the red [COLOR="#FF0000"]Go Advanced[/COLOR] button below the editing window to reply in this thread.

Read the file into an editor (gedit in standard Ubuntu)

```
gedit  lshw.txt
```

copy and paste from the editor window to the editing box of the Ubuntu Forums thread. Mark this text and click on the # icon above the editing box to put it within code tags

[noparse]```

the output text,
can be several lines
...

```[/noparse]

(or edit those code tags manually). This makes it easy for us to read about your computer's hardware, and it will help us help you.

---

### Post by geogur on 2016-07-07
so im replacing my chip set and vidio card , what is a linux friendly card i have a 694 GEForce 9600 GT (navidia) ifound out it was not linux friendly 

if i get a core 5 or better and a new vidio card i think i can then upgrade ,

---

### Post by sudodus on 2016-07-08
Users of new graphics cards, please suggest a linux friendly one for *geogur* :-)

---

### Post by geogur on 2016-07-09
thinking strix r9 fury dc3 46 gaming  AMD to replace my 

g94 geforce9600gt nvidia 

AMD i think is a better choice than nvidia (saw a vid of linus saying f#$% y@# nvidia)
so im thinking AMD this time . my 9600gt still has driver support but age has crept up on my aged set up

---

### Post by geogur on 2016-07-18
so get a new vidio card and am using a fresh hd and still crashes , whats next motherboard ?

---

### Post by sudodus on 2016-07-19
1. Please describe with as many details as possible what happens! (Describe what you see and hear before and at the crash.)

2. Please try with a ***live*** session booted from a DVD or USB drive. Does it start working? Can you do 'all the things you want to do' with the computer? Or does it crash similar to what happens with an installed system.

See this link and links from it: [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

---

