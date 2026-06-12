---
title: "Ubuntu Install CD (12.04) Hangs On First Screen"
date: 2013-07-10
forum: Installation &amp; Upgrades
---

### Post by PCunicorn on 2013-07-10
My 12.04 LTS install CD is hanging on very first screen. The purple one with the guy with arms and legs outstretched in a circle with a equal sign to the left that points to another icon. It's also the one that comes before the orange dots.

---

### Post by su:bhatta on 2013-07-10
OK, try this out and then inform....

On the first boot from the Ubuntu DVD you will find a **purple screen with a Man=keyboard** sign at the bottom of the screen:

1)At that screen you hit **Enter**...
it gives you a next screen where by default you will get a list of languages with English selected as default..

2)on that screen select English/or what you want---> hit enter... It will get you the Try Ubuntu/Install Ubuntu Screen

at the bottom of the screen you will see options underneath F1 F2 F3 etc.. ... **Hit F6** on that screen.. 
You will see a **pop up Box** at the bottom of the screen... use the arrow keys to go down to: "**NOMODESET**" hit enter... **a small Cross(X) **will appear beside 'nomodeset'

3)Press escape

Then choose Try/Install 
It should just boot up fine ....

BTW, All 'nomodeset' does is, it stops installing the video drivers at the beginning...
if you r using AMD, you may have to download proprietary drivers(Once installed) to get the right screen resolution n all....

---

### Post by PCunicorn on 2013-07-10
Okay, I did that and now when I hit install Ubuntu it hangs.

---

### Post by BreezyBrooke on 2013-07-10
What are your PC Specs? CPU, Graphics, or just your computer's model number will do. Also, what copy of 12.04 is it? 32bit or 64bit?

---

### Post by PCunicorn on 2013-07-10
32 Bit. PC specs are: Athlon 1333C (around a first generation P4), Radeon 9600 SE, 512 MB DDR RAM, built by me quite a few years ago. I know it's old, but it runs 10.10 fine, and it's all I have until I save up enough for a new one.

---

### Post by BreezyBrooke on 2013-07-10
Thats why. Your PC is too old and weak. Ubuntu needs A BARE MINIMUM of 1GB to run. Any less and the installer hangs as well as 1GB minimum is needed to run ubuntu anyways. Also, that GPU isn't supported anymore so you will be running the default, open source graphics driver, which is slow, and that CPU will make Ubuntu run like poo. Sorry, but you cannot run Ubuntu on that thing. Try Lubuntu or Xubuntu. They should work fine.

You have to realize Ubuntu is a powerhouse OS that needs really good hardware to run. Anything Computer older than the Core 2 Duo/Athlon 64x2 era of CPU's tends to be too weak to run Ubuntu at full speed.

---

### Post by PCunicorn on 2013-07-10
It wasn't like that on 10.10.

---

### Post by BreezyBrooke on 2013-07-10
Well, PCunicorn, It has been two and a half years since 10.10. A lot has changed for Ubuntu and the computing world at large since that time. It's just a fact of progression and new technological advancements. As stated, Xubuntu and Lubuntu should run fine on your old PC, but Ubuntu will not. Too heavy and demanding. Xubuntu and Lubuntu were built with old PC's in mind, while as Ubuntu is to the future.

---

### Post by PCunicorn on 2013-07-10
Well, W8 looks towards the future and it requires LESS demanding specs the 7. And, unity sucks. Ubuntu 12.04 CAN run on my PC with Gnome, and I need it for the network modules.

---

### Post by PCunicorn on 2013-07-10
Will xubuntu run on my PC?

---

### Post by BreezyBrooke on 2013-07-10
First off, Windows does not equal Ubuntu. Just because Windows 8 needs less, dosen't mean Ubuntu does. Anyways, look at Win8. Why do you think it needs less? It's all flat graphics and simple 2d stuff, a childs toy. As well as Win8 was built for tablets initially. Of course it uses less. But Ubuntu on the otherhand realizeses a modern PC is more than just "a toy" and gives you a real meat and potatoes OS that does a lot and looks great. Even if you install the Gnome desktop in Ubuntu on your PC **IT WILL STILL BE TOO MUCH FOR IT.** Even Gnome shell has high demands. Even Gnome session fallback may be a bit over. Either use Xubuntu or Lubuntu, or buy a new PC. If you don't like those options, move elsewere. Fedora has some of the best networking tools availble. Try their LXDE spin. Sorry if I sound rude, just trying to be helpful.

Edit: Yes, Xubuntu will run.

---

### Post by su:bhatta on 2013-07-11
PCUnicorn, really sorry my idea didn't work out... I thought u had some graphics card problem...

Plz check this page for Xubuntu 12.04 system requirements.. it says it runs with 512 MB ram...
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Xubuntu](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/Xubuntu)

---

### Post by claracc on 2013-07-11
I would consider to try lubuntu, which is ubuntu software for old machines.

Minimum requirements: [https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes/Lubuntu](https://wiki.ubuntu.com/RaringRingtail/ReleaseNotes/Lubuntu)

What kind of network moules do you need?

---

