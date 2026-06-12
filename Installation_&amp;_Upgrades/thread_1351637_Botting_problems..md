---
title: "Botting problems."
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by Ganjafreak on 2009-12-10
I recently installed XP and ubuntu on the same pc well I finally got to get around to updating my Ubuntu cause I've had court this week I get on it and Do the updates then the hardware graphic driver and I click restart it loads back up I log back in and it shows me the mouse for 2 secs then says SOMETHING input out of range change to 1280x something

Can someone tell me how to get it back like in the recovery mode or something cause I can't even get on it at all. I'm having to make this thread with my XP.

---

### Post by Ganjafreak on 2009-12-11
I really need help with this as I'm doing a school homework assesment and I need to make a couple of docuement and sounds to go with them.

---

### Post by oldos2er on 2009-12-11
Have you tried booting into recovery mode, and running **sudo dpkg-reconfigure -phigh xserver-xorg** ?

---

### Post by Ganjafreak on 2009-12-11
Nope, You just saved me from reinstalling cause no one was posting

Is there like a list of sudo's or something where do people get them from

all these fixes?

---

### Post by Ganjafreak on 2009-12-11
Last time I reinstalled I'm not sure but I installed my graphics driver and when I rebooted automatically made it go outof range I'm not sure if I edited it or what can't remember.

But, If I were to reboot right now and it automatically puts me out of range(which hasen't in the past)(I've reinstalled my desktop with ubuntu 7 times) but what is the code to make it assign say that 1280x600 resolution or what ever is in that 1280 range

I think it's 
1280x8?? or something close to that.

---

### Post by oldos2er on 2009-12-12
What video card do you have?

---

### Post by Ganjafreak on 2009-12-12
I have a Nvidia Geforce 6275 I think
How do I tell, I'm in windows at the moment.,

---

### Post by oldos2er on 2009-12-12
In Windows, isn't there something called Device Manager? Maybe that would tell you. Or you can boot Ubuntu recovery mode and run **lspci**.

---

### Post by Ganjafreak on 2009-12-12
Okay, I will boot in recovery and run that code. What will that do? Reconfigure it to the max of my screen or something?

And there is something called Device Manager, It lists everything that is connected or is on your computer

---

### Post by Ganjafreak on 2009-12-13
Okay that lspci all that does is reset me back to the normal, Once I reinstall that recommended graphics driver and restart it will say input out of range again

I have a Geforce 6150 le Is there a xorg file that someone has that I could just edit my file with theres. I need a max setting of 1280x1028 60hz

Is there someway I could code that into my own xorg file or something???

Now I was using ubuntu for about 3-4 months, It wasn't doing the input out of range unless I went out of range on purpose by clicking a diffrent setting why all of a sudden is this doing it?????

I have installed XP first then ubuntu, I did that before. So nothing is new so why all of a sudden is it doing it.,

It couldn't have anything to do with a lose cord or something? Should I plug in another display cord that runs to my monitor to pc?

---

### Post by Ganjafreak on 2009-12-13
Now, I just poped up my Hardware drivers

It says I have a diffrent version of driver 173 in use

I want the recommended one. I'm about to install that one and see if I cant go to display and edit it to 1280 automatically without having to reinstall and have it do it for me

---

### Post by oldos2er on 2009-12-13
> **Ganjafreak said:**
> Okay, I will boot in recovery and run that code. What will that do? Reconfigure it to the max of my screen or something?


 lspci will show you your hardware.

---

### Post by oldos2er on 2009-12-13
You can try **envyng-gtk** to install the appropriate driver also.

---

### Post by Ganjafreak on 2009-12-13
> **oldos2er said:**
> You can try **envyng-gtk** to install the appropriate driver also.

With this, do I run it in recovery or what

And does this install the right driver and choose MY max screen resolution not the worlds max biggest monitor. Cause I believe it went to 10,000x9589

I'm thinking it did.

---

### Post by oldos2er on 2009-12-13
If you run envyng in recovery mode, I believe the command would be envgng-core. Sorry, it's been a long time since I've used it.

---

### Post by Ganjafreak on 2009-12-13
I ran the code you gave me earlier. The other envy one and it said unknown command.

---

