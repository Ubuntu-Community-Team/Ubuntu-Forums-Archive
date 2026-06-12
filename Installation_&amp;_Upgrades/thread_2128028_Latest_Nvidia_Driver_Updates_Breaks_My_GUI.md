---
title: "Latest Nvidia Driver Updates Breaks My GUI"
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by ezacharyk on 2013-03-21
I am running Ubuntu 12.04 64bit. The other day, the reccommended updates had an Nvidia driver update with it. I ran the updates like I do every time they popup. Yesterday, I turned on my computer for the first time after shutting down when the updates completed. Instead of the usual GUI login screen, I was presented with the terminal comand prompt.

I have been racking my brain all day and the only thing that provides any change is purging Nvidia from my computer using the following script:

```
sudo apt-get purge nvidia* && sudo apt-get autoremove

```

Doing this and restarting presents me with the GUI, albeit in a very cramped 1024x768 screen resolution. That and 800x600 are the only options available to me in the Display settings window. Prior to this latest update, I could go all the way up to 1920X1080. 

I am running an Asus laptop with a Core i7 CPU and an Nvidia Geforce GTX 660M graphics card. 

I tried using all the available Nvidia drivers in the Additional Drivers section. Of course none of the available drivers have names that I recognize from before the update. 

Any help in getting the Nvidia drivers working would be great. Programming and gaming just can't happen in my current state.

---

### Post by papibe on 2013-03-21
Hi ezacharyk.

Is there an 'nvidia-current' version? I'd recommend that.

If not, could you post a screenshot of the options offered to you?

Regards.

---

### Post by ezacharyk on 2013-03-21
I tride running "sudo apt-get install nvidia-current" in terminal and after rebooting, I was back where I started with no GUI.

Here are my driver options:

[IMG]http://ezknight.net/wp-content/uploads/2013/03/add_driver_options.png[/IMG]

---

### Post by ezacharyk on 2013-03-21
sorry, double post.

---

### Post by papibe on 2013-03-21
Try this running this:
```
sudo nvidia-xconfig
```
then restart.

Let us know how it goes.

---

### Post by ezacharyk on 2013-03-21
> **papibe said:**
> Try this running this:
```
sudo nvidia-xconfig
```
then restart.

Let us know how it goes.

That did it. I had to install the nvidia-current driver first. But I am back in action. Thanks for the help.

---

