---
title: "Testing Ubuntu Beta Releases off the USB stick"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by shanix on 2009-09-23
Hi Everyone,

I wrote a little script to help testing the beta releases without actually upgrade the machine, hope someone find it useful.

**Requirement:**
0. **[COLOR="DarkOrange"]BACKUP YOUR HOME DIRECTORY...[/COLOR]**
(The script doesn't touch your home partition, but after linking your home directory to the USB stick, any software changes you made will write to your home partition. So, it is always a good idea to make a backup first!)

1. One 4G or more USB stick 

2. Download the Karmic or later Beta CD from here: 
[http://cdimage.ubuntu.com/releases/karmic/](http://cdimage.ubuntu.com/releases/karmic/)

[B]
Goal: [/B]

1. Better Upgrade Experience

2. Hardware Testing from the usb stick before actually upgrade the machine
	a. Networking - Wireless, Wired 
	b. Display - Right Resolution, Compiz, 
	c. Sound - Speaker, Internal/External Microphone
	d. Webcams 

3. Run the script to link your home directory to the USB stick and test the software compatibility with the beta release

4. If everything going well, then upgrade your system to the beta releases


**Instruction:**

1. You need to download the latest karmic image from:
[http://cdimage.ubuntu.com/releases/karmic/](http://cdimage.ubuntu.com/releases/karmic/)

2. Follow the docs from ([http://dl.getdropbox.com/u/2101775/Install_Ubuntu_beta_on_USB.pdf](http://dl.getdropbox.com/u/2101775/Install_Ubuntu_beta_on_USB.pdf)) and installed it your 4G (or more) USB stick

3. Change the BIOS setting if needed and boot the machine from the USB stick

4. Testing your hardware compatibility with the beta releases

5. Run the script to link your home directory to the USB stick, reboot.

6. Boot from the USB stick and test the hardware and software compatibility again.

7. If everything works as expected, then upgrade your system to the beta releases by running:

sudo update-manager -d

or 

sudo do-release-upgrade -d


**Usgae of the script:**

1. The script will detect how many Ubuntu releases that you have installed on the machine, if

a. You only have one installed, it will present you the option to confirm the home directory to link to the USB stick

b. If there is more than one, it will present you the the options and let you make the selection.
[B]
How to run the script:[/B]

1. Download the script to your home directory when booting from the USB stick.

2. Make it executable by Right Click On The File> Select Properties> Select the Permissions Tab. Now, enable the "Allow executing file as program" checkbox. Close the window, double click on the file and select "Run in Terminal."


**Q & A:**

Things doesn't work as expected?

Since the grub is installed on your USB stick, and the script only mount/link your home directory to the USB stick, if anything doesn't work as expected. You just need to simply reboot the machine and everything will be back to normal.

Boot from the USB stick again on different machine after running the script?

The script will create the link and rename the home directory on your USB stick, and modify your /etc/fstab. To reverse the changes, you will need to do the following two things:
1. Restore your fstab file on the USB stick:
a. Look under your /<mount point of your usb stick>/etc directory, the backup of your fstab is called fstab.2009xxxx
b. You can move it back by running: 
sudo rm /<mount point of your usb stick>/etc/fstab; sudo mv /<mount point of your usb stick>/etc/fstab.2009* /<mount point of your usb stick>/etc/fstab

2. Restore your home directory on the USB stick:
a. The old home directory will be renamed to home.usb, so to rename it back, you can run the command:
sudo mv /<mount point of your usb stick>/home.usb /<mount point of your usb stick>/home

---

