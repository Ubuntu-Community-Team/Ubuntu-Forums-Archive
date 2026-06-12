---
title: "A Noob Question From A Noob"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by MamuMogambo on 2013-04-04
I have a bootable Ubuntu USB. 
Question is:
Do I have to install Ubuntu onto my HDD to use all the Ubuntu features? Can I do all the things from the USB that I'd be able to do from the HDD or is there a difference (most probably there is, I know)?
What are the differences?

---

### Post by slickymaster on 2013-04-04
All your questions are answered [here]("https://help.ubuntu.com/community/LiveCD") and [here]("http://www.ubuntu.com/download/help/try-ubuntu-before-you-install").

---

### Post by MamuMogambo on 2013-04-04
> **slickymaster said:**
> All your questions are answered [here]("https://help.ubuntu.com/community/LiveCD") and [here]("http://www.ubuntu.com/download/help/try-ubuntu-before-you-install").
Thank you Slickymaster

---

### Post by slickymaster on 2013-04-04
Don't forget to mark the thread as SOLVED.

See my signature if you have doubts on how to do it.

---

### Post by MamuMogambo on 2013-04-04
> **slickymaster said:**
> Don't forget to mark the thread as SOLVED.

See my signature if you have doubts on how to do it.
I cannot marked it solved. I still have doubts. Would like a straightforward answer

---

### Post by bogan on 2013-04-04
> **MamuMogambo said:**
> I have a bootable Ubuntu USB. 
Question is:
Do I have to install Ubuntu onto my HDD to use all the Ubuntu features? Can I do all the things from the USB that I'd be able to do from the HDD or is there a difference (most probably there is, I know)?
What are the differences?Hi!, Welcome to the Forum!

If your bootable USB is a full installation it is no different in its functions from if installed on an HDD, The only difference is in available storage space and the speed of operation for some functions, especially if you are short of Ram, say less than 2 GB.

On my not very new computer Booting up takes only 10% longer from an USB2, than from an HDD internal or external; at the other extreme the 'Loading Software List' function of the Software Updater, which takes about 5 secs to the HDD, takes more than 45 seconds to the USB. Updating and Upgrading take similarly longer.

If your USB is burnt from an .iso it is a LiveCD/Usb and booting from that is a good way of checking if there are problems with your hardware, but is not practical for everyday use: it will not retain any additions, changes, configurations, or driver installations, after a reboot, as it runs from a ramdisk.

So the answer to your first question is : No, not just for occasional use to run all the features included by default; but: Yes, if you want **ALL** the Ubuntu features available. There are many additional, essential features, that must be installed separately. So those you would need to reinstall each time after a shutdown, if it is a LiveUSB.

Chao!,** bogan**. Edit; Posted before reading Posts after the OP.

---

### Post by slickymaster on 2013-04-04
Simple, just go to the first post in this thread and click on "Edit Post", then click on the orange "Go Advanced" button and in the advanced editor change the prefix to "SOLVED". Finally click on the orange "Save Changes" button.

---

### Post by MamuMogambo on 2013-04-04
Thanx Bogan, one more question though:
I have a bootabale Ubuntu USB, I want to install a few softwares from the Software Center (like Synaptic Package Manager) but instead of the "Install" button I am getting "Use This Source". Is it because I am using bootable USB?

---

### Post by MamuMogambo on 2013-04-04
Also, many Terminal commands don't work, like sudo apt-get. I always get "unable to locate package"

---

### Post by bogan on 2013-04-04
Hi!, **MamuMagambo**.

To install additional features to the Bootable USB it needs to be one to which Ubuntu has been installed, not a LIVE/USB burnt from an .iso or [ I think, ] made by Startup Disk Creator.

Try, from a Terminal -'Ctrl+Alt+t' -: ```
sudo apt-get install synaptic
synaptic # to actually use it you need to add 'sudo'
```And see what happens. You should get the Synaptic Package manager display with a warning window.

Then reboot and see if Synaptic is still there, either from a terminal or from the Dash Launcher. if it is not, see my previous Post.

Edit; RE your Post #9, Make sure you have the exact packagename correct. Run:```
 sudo apt-get update 
#what error messages do you get, with this or with:
sudo apt-get install synaptic
```Chao!, **bogan**.

Reson for edit: note added

---

### Post by MamuMogambo on 2013-04-04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate



This is what I am getting

---

### Post by slickymaster on 2013-04-04
Synaptic is available in the so-called universe repository. If you cannot find that package, it means that you do not have universe enabled.
I'm assuming that you are using Quantal (12.10), so to enable it, open **Software Sources** and select **Community-maintained free and open-source software (universe)**.
After doing so, you will be asked to reload the software sources and you will be ready to install your package.

---

### Post by bogan on 2013-04-04
Hi!, **MamuMogambu, **

See my post #10 Edit note.

What ubuntu distribution and version are you running ?```
uname -ar
```

What happens if you use 'Ctrl+Alt+F1' and login there and use the terminal commands ? ['Ctrl+Alt+F7'should take you back to the GUI].

Chao!, **bogan.**

---

### Post by MamuMogambo on 2013-04-04
I have started the updates, I think they are quite important and I am having problems because I haven't installed a single update (also, I am using a usb wcreated with the Ubuntu ISO)

---

### Post by MamuMogambo on 2013-04-04
I have Ubuntu 12.10

---

### Post by MamuMogambo on 2013-04-04
Hey I install the updates and the sudo command is working fine now. I am going to check the software center now

---

### Post by MamuMogambo on 2013-04-04
Thanx guys everything is working fine after installing the updates.
So the thing is I can use a bootable USB without any problem
Thanx Bogan and slickymaster

---

### Post by slickymaster on 2013-04-04
Glad you got it working, that's what's important.

---

### Post by MamuMogambo on 2013-04-04
A superthanx again slickymaster and bogan for all the help

---

