---
title: "The perfect MythTV install for Dapper using MythTV 0.19"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by HJB on 2006-06-11
Hi all. I have been reading for days now, but everywhere I only find patched howtos to do a mythyv install on dapper. I downloaded KnoppMyth which is great but what I have agains it is its not ubuntu (mmmm) and I dont know where what happens, it just do.

So I decided to do it on my own.

I will post a list of thank you's to great pages who have helped me along.
This is not finished. Might finish it up tonight (myth starts but I dont have access to mysql). I should figure it out later and update this post.

If you want to help me perfect what I refer to as "mythbuntu" (so sue me), PLEASE do so and help to make this script great

Here is what I have so far:
The script and the altered sources.list should go into a directory like 'mythinstall'
Save it as anything(I used bashmyth.sh)
run it with 'sudo sh bashmyth.sh'

It is set up do firstly do a dummy run where nothing happens, so it will not brake your system. 
Change the script to DUMMY=OFF should you want to run it for real.


> 
#!/bin/bash
# By HJB 11-06-2006

#save it as something like bashmyth.sh in a directory under home, like mythinstall

	
wait_for_user () {
	input=""
	echo " "
	echo " "
	echo "Press [space] to continue..."
	
	until [ "$input" = "ok" ]
	do
	read -srn1
	if [ -n "$REPLY" ]; then
		input="ok"
	fi
	done
	input=""
	clear
}

install_ubuntu () {
	echo " "
	echo "GET AND INSTALL UBUNTU:"
	echo " "
	clear
	echo "This script is intended to run on a newly formatted ubuntu machine BUT can also run on your current system should you want to just install ivtv or something similar."
	echo " "
	echo "Firstly we need an OS"
	echo "Get hold of ubuntu. I used xubuntu."
	echo " "
	echo " "
	echo "Do you want to download a new ubuntu iso to this machine now? (usually you answer 'n'o here ):"
	echo "Type Y or n"

	until [ "$input" = "ok" ]
	do
	read 
	if [ $REPLY = "Y" ]; then
		echo "Starting to download"
		input="ok"
		$DUMMY wget -c [http://cdimage.ubuntu.com/xubuntu/daily/current/dapper-alternate-i386.iso](http://cdimage.ubuntu.com/xubuntu/daily/current/dapper-alternate-i386.iso) # change here should you require another version
		wait
		else
			if [ $REPLY = "n" ]; then
				echo "Ok moving along"
				input="ok"
				else
					echo "Only Y or n"
					input=""
			fi
	fi
	done
	input=""
	wait_for_user
	echo "Ok now you have to burn this iso to a cd and boot from there!"
	echo " "
	echo "If the cd boots up with a nice graphical interface press 'escape' and answers 'ok' to change to text base booting "
	echo " "
	echo "At the boot prompt press enter or type a cheat code should you require one (type F3 for more info)"
	wait_for_user
	echo "Now select your language, loaction and keyboard"
	echo "Wait for some prosessing..."
	echo "Get your network working!!!"
	echo "Select hostname"
	echo "Select 'manually edit partition table' and set it up to the one below"
	echo " "
	echo "MountPath	Type		Size"
	echo "/		ext3		5%	Bootable, Format"
	echo "swap		swap		2x size of ram (eg. 512 ram = 1024MB) "
	echo "/myth		xfs		Remainder of drive"
	echo " "
	echo "Select finish and write changes to disk"
	echo "Answer qustion regarding system clock"
	echo "Fill in new user, user name and password"
	echo " "
	echo "wait for installation to finish"
	echo "When finished log in with new username and pass"
	wait_for_user
}

start_on_new_box () {
	echo " "
	echo "STARTING ON YOUR NEW BOX:"
	echo " "
	echo "Copy this script to the the new computer which you just installed ubuntu on"
	echo "You can use your own initiative ): or use"
	echo "wget -c http://<place where you found this script>"
	echo "or if you are lucky enough to have another linux box type 'sudo apt-get install openssh-server' on the new box and when the install finishes,"
	echo "go to the other (old) box and transfer this script to the new myth box"
	#do 'ssh <new_username_of_myth_box>@new_ip_address' example (ssh peter@192.168.1.5)"
	echo " "
	echo "Ok so I want you to be on the new box either via ssh or on the box itself."
	echo "Now the fun begins!"
	echo " "
	echo "Are you on the new box, ready to begin?"
	echo "Type Y or n"

	until [ "$input" = "ok" ]
	do
	read 
	if [ $REPLY = "Y" ]; then
		echo "Goody!!!"
		input="ok"
		else
			if [ $REPLY = "n" ]; then
				echo "Ok exiting...."
				exit
				input="ok"
				else
					echo "Only Y or n"
					input=""
			fi
	fi
	done
	input=""
	wait_for_user
}

install_xfce () {
	echo " "
	echo "INSTALLING XFCE4:"
	echo " "
	echo " "
	echo "If you did a full install the following is not necessary..."
	echo "However,"
	echo "I want to install the basic Xfce Windows manager."
	echo " "
	echo "Should I continue?"
	echo "Type Y or n"	
	until [ "$input" = "ok" ]
	do
	read 
	if [ $REPLY = "Y" ]; then
		echo "Good"
		$DUMMY sudo apt-get install x-window-system-core xfce4
		wait
		input="ok"
		else
			if [ $REPLY = "n" ]; then
				echo "I hope you have one installed ):"
				input="ok"
				else
					echo "Only Y or n"
					input=""
			fi
		fi
		done
		input=""
		wait_for_user
}

install_nvidia () {
	echo " "
	echo "INSTALLING LATEST $MY_NVIDIA DRIVERS:"
	echo " "
	echo "Good, now I suggest you update your nvidia drivers, if this is what you use."
	version=8762 # change this if you have another one you want to install
	echo " "
	echo "If you answer no, we'll use your existing drivers"
	echo " "
	echo "Dont worry to much if errors present here which complain about files not found"
	echo "Remember that restricted-modules will be removed."
	echo "If you dont know what this mean dont worry."
	echo " "
	echo "should we do this now?"
	echo " "
	echo "Type Y or n"
	until [ "$input" = "ok" ]
	do
	read 
	if [ $REPLY = "Y" ]; then

		echo "Ill get version "$version "from nvidia's website"
		$DUMMY sudo /etc/init.d/gdm stop
		$DUMMY mkdir -p ~/$MY_NVIDIA
		$DUMMY cd ~/$MY_NVIDIA
		$DUMMY wget -c http://download.nvidia.com/XFree86/Linux-x86/1.0-$version/NVIDIA-Linux-x86-1.0-$version-pkg1.run
		$DUMMY sudo apt-get install build-essential gcc linux-headers-`uname -r`
		$DUMMY sudo apt-get --purge remove linux-restricted-modules-`uname -r` linux-restricted-modules-common nvidia-glx nvidia-settings nvidia-kernel-common
		$DUMMY sudo rm /etc/init.d/nvidia-*
		$DUMMY sh NVIDIA-Linux-x86-1.0-$version-pkg1.run --extract-only
		$DUMMY cd NVIDIA-Linux-x86-1.0-$version-pkg1
		$DUMMY sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_1_$version
		$DUMMY sudo ./nvidia-installer -n --x-prefix=/usr/lib/xorg/
		$DUMMY sudo cp /usr/lib/xorg/lib/libX* /usr/lib/xorg/modules/
		$DUMMY sudo cp /usr/lib/xorg/lib/modules/drivers/* /usr/lib/xorg/modules/drivers/
		$DUMMY sudo cp /usr/lib/xorg/lib/modules/extensions/* /usr/lib/xorg/modules/extensions/
		$DUMMY sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup_2_$version
		$DUMMY sudo rm -r N*$version*pkg1
		$DUMMY cd ~/$MY_DIRECTORY
		$DUMMY sudo /etc/init.d/gdm start
		$DUMMY cd
		wait
		input="ok"
		else
			if [ $REPLY = "n" ]; then
				echo "Ok continuing..."
				input="ok"
				else
				echo "Only Y or n"
				input=""
			fi
	fi
	done
	input=""
	wait_for_user
}

change_sources_file () {
	echo " "
	echo "UPDATING SOURCES.LIST FILE:"
	echo " "
	$DUMMY sudo cp /etc/apt/sources.list /etc/apt/sources.list.mythbackup
	clear
	echo "A backup was made of your sources.list file."
	echo " "
	echo "If you have no clue what the following mean, dont worry and say yes, 'Y'"
	echo " "
	echo "Should I over write your current sources.list file with a new one?"
	echo " "
	echo "Type Y or n"
	
	until [ "$input" = "ok" ]
	do
	read 
	if [ $REPLY = "Y" ]; then

		echo "Copying new file to sources.list and thus changing it now."
		$DUMMY sudo cp sources.list /etc/apt/
		input="ok"
		else
			if [ $REPLY = "n" ]; then
				echo "Ok doing nothing. This should work if you wnat to do it manually"
				echo "Just add these lines to the file"
				echo "deb     [http://www.hellion.org.uk/debian](http://www.hellion.org.uk/debian) sid main"
				echo "deb-src [http://www.hellion.org.uk/debian](http://www.hellion.org.uk/debian) sid main"
				echo " "
				input="ok"
			else
				echo "Only Y or n"
				input=""
			fi
	fi
	done
	input=""
	wait_for_user
	echo "Doing an update of the repository now."
	echo " "
	$DUMMY sudo apt-get update 
	input=""
	wait_for_user
}

install_personal_stuff () {
	clear
	echo " "
	echo "INSTALLING PERSONAL STUFF:"
	echo " "
	echo "Ok at this point I want to install a few personal favorites which is always neccesary on a linux box ):   (go ahead, flame me!!!)"
	echo " "	
	echo "They are not vital to this installation"
	echo " "
	echo "Some might already be in here..."
	echo "They are slocate, synaptic and openssh-server"
	echo "Do I do so or not?"
	echo " "
	echo "Type Y or n"
	until [ "$input" = "ok" ]
	do
	read 
	if [ $REPLY = "Y" ]; then
		echo "Ok"
		$DUMMY sudo apt-get install synaptic slocate openssh-server
		wait
		echo " "
		echo "Running slocate for the first time, please wait a few seconds..."
		echo " "
		$DUMMY sudo /etc/cron.daily/slocate
		$DUMMY sudo slocate -u
		wait
		echo "Ok finished, tnx for waiting ):"
		input="ok"
		else
			if [ $REPLY = "n" ]; then
				echo "Its your box ):"
				input="ok"
				else
					echo "Only Y or n"
					input=""
			fi
	fi
	done
	input=""
	wait_for_user
}

install_ivtv () {
	echo " "
	echo "INSTALLING IVTV:"
	echo " "
	echo "Ok now we have to get some files which are going to be needed further along."
	echo " "
	echo "			build-essential"
	echo "			gcc"
	echo "			linux-headers-"`uname -r`
	echo "			ivtv0.4-source"
	echo "			module-assistant"
	echo "			dpkg-dev"
	echo "			libconfig-inifiles-perl"
	echo "			libvideo-ivtv-perl"
	echo "			unzip"
	echo " "
	echo "Should I get them?"
	echo "Type Y or n"	
	until [ "$input" = "ok" ]
	do
	read 
	if [ $REPLY = "Y" ]; then
		echo "Ok"
		$DUMMY mkdir -p ~/ivtv
		$DUMMY cd ~/ivtv
		$DUMMY sudo apt-get install build-essential gcc linux-headers-`uname -r` ivtv0.4-source module-assistant dpkg-dev libconfig-inifiles-perl libvideo-ivtv-perl unzip
		wait
		echo "Next, we tell module-assistant to get all dependancies. This will automatically get all required kernel headers and associated packages."
		$DUMMY sudo module-assistant prepare
		wait
		echo "Now you need to compile the driver into a package:"
		$DUMMY sudo module-assistant auto-install ivtv0.4
		wait
		$DUMMY sudo apt-get --compile source ivtv0.4-utils
		wait
		$DUMMY sudo dpkg -i ivtv0.4-utils_0.4*i386.deb
		echo "Now we go get the lates firmware"

# see page [http://ivtvdriver.org/index.php/Firmware](http://ivtvdriver.org/index.php/Firmware)
# quote 
# For ivtv 0.4.0 and earlier, this is:
# cp HcwMakoC.ROM /lib/modules/
# cp HcwFalcn.rom /lib/modules/ivtv-fw-enc.bin
# and for ivtv 0.4.1 and later, this is (remember, the names below are vee-four-el, not vee-four-one):
# cp HcwMakoC.ROM /usr/lib/hotplug/firmware/v4l-cx25840.fw
# cp HcwFalcn.rom /usr/lib/hotplug/firmware/v4l-cx2341x-enc.fw
# BUT The easiest way to obtain the firmware files is to simply download this file: [http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz)

		$DUMMY wget -c [http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/firmware.tar.gz)
		$DUMMY sudo tar zxvf firmware.tar.gz -C /lib/firmware/
		wait
		wait_for_user	
		input="ok"
		else
			if [ $REPLY = "n" ]; then
				echo "You'r the boss..."
				echo "Not a good choice though, unless you are running this script again and have done this step before."
				input="ok"
				else
					echo "Only Y or n"
					input=""
			fi
	fi
	done
	input=""
	echo "The following should appear, if you started from a clean box"
	echo " "
	echo "total 820"
	echo "-rw-r--r--  1  505  502  16382 2006-05-26 11:35 v4l-cx25840.fw"
	echo "-rw-r--r--  1  505  502 376836 2006-05-26 11:35 v4l-cx2341x-enc.fw"
	echo "-rw-r--r--  1  505  502 262144 2006-05-26 11:35 v4l-cx2341x-dec.fw"
	echo "-rw-r--r--  1  505  502 155648 2006-05-26 11:52 v4l-cx2341x-init.mpg"
	echo "drwxr-xr-x  2 root root   4096 2006-06-03 23:43 2.6.15-23-386"
	echo "drwxr-xr-x 17 root root   4096 2006-06-03 23:43 .."
	echo "drwxr-xr-x  3 root root   4096 2006-06-04 12:03 ."
	echo " "
	echo " "
	echo "And this should look like the following"
	$DUMMY cd /lib/firmware
	$DUMMY ls -ltra
	wait
	$DUMMY cd ~/$MY_DIRECTORY
	wait_for_user
}

setup_ivtv () {
	echo " "
	echo "SETTING UP IVTV:"
	echo " "
	echo "Ok now for some trickey stuff"
	echo "$MY_EDITOR (editor) will open now."
	echo "Copy this line into the file that opens, (alias char-major-81-0 ivtv)  so that it looks something like this:"
	echo "Save it and close $MY_EDITOR"
	echo "alias char-major-75-* specialix"
	echo "alias char-major-76-* specialix"
	echo "alias char-major-81-* videodev"
	echo "alias char-major-81-0 ivtv"
	echo "alias char-major-83-* vtx"
	echo "alias char-major-89-* i2c_dev"
	echo " "
	echo " "	
	echo "I suggest copying and pasting"
	wait_for_user
	$DUMMY sudo $MY_EDITOR /etc/modprobe.d/aliases
	wait
	echo " "
	echo "Are you finished editing that file?"
	echo "Type Y or n"
	until [ "$input" = "ok" ]
	do
	read 
	if [ $REPLY = "Y" ]; then
		clear
		echo "Ok, kewl."
		echo "If, at the end of the following output of dmesg, you see a section starting with ==START INIT IVTV== "
		echo "and ending with ==END INIT IVTV==, you are in good shape"
		echo " "
		echo "as long as the text in between these markers is not filled with errors. ):"
		input="ok"
		#wait_for_user
		else
			if [ $REPLY = "n" ]; then
				echo "Not a good choice, exiting....."
				exit
				else
					echo "Only Y or n"
					input=""
			fi
	fi
	done
	input=""
	echo "Do you want to execute depmod now?"
	echo " "
	echo "Type Y or n"	
	until [ "$input" = "ok" ]
	do
	read 
	if [ $REPLY = "Y" ]; then
		echo "Ok"
		$DUMMY sudo depmod
		input="ok"
		else
			if [ $REPLY = "n" ]; then
				echo "Not a good choice, unless you are running script again and have done this step before."
				input="ok"
				else
					echo "Only Y or n"
					input=""
			fi
	fi
	done
	input=""
	$DUMMY sudo modprobe ivtv
	$DUMMY dmesg
	wait_for_user
}

final_words () {
        clear
	echo " "
	echo "FINALIZING:"
	echo " "
        echo "Ok by now you should have:"
	echo "1. A working copy of ubuntu."
        echo "2. New nvidia drivers from their website and builded fresh"
        echo "3. A new sources.list file with an updated repository"
        echo "4. A newly complied ivtv driver and firmware"
	echo " "
	echo "What is needed now is mythtv 0.19"
	echo "If you are on a new freshly formatted box which you dont mind to crash (cause Im still strugling to install mythtv 0.19 nicely), type in 'Continue' (without the quotes BUT with a Capital C)"
	echo "Otherwise type 'n' (good choice at this stage)"
	echo "Type Continue or n"	
	until [ "$input" = "ok" ]
	do
	read 
	if [ $REPLY = "Continue" ]; then
		echo "Living on the edge..."
	
		input="ok"
		else
			if [ $REPLY = "n" ]; then
				echo "Look back at the place where you found this script for regular updates and to go on from here."
				input="ok"
				else
					echo "Only Continue or n"
					input=""
			fi
	fi
	done
	input=""
        wait_for_user

}


admin () {
#Check to see if you are root or not
if [ `id -u` != "0" ]; then
        echo "Sorry, you are not root."
        exit 1
fi
# change the following three lines to the ones you want##################################
MY_EDITOR=nano #your personal favorite							#
MY_DIRECTORY=mythinstall # set the same as the on you are running this script from
MY_NVIDIA=NVIDIA	#
DUMMY=OFF										#
# Should you want to run it for real just change ON to OFF				#
#########################################################################################
clear
echo " "
echo "You have chosen (settings in the script) to:"

if [ $DUMMY != "OFF" ]; then
	if [ $DUMMY != "ON" ]; then
		exit
	fi
fi

if [ $DUMMY = "OFF" ]; then
	echo "1. Run this script for real (not a dummy run)"
	DUMMY=""
fi

if [ $DUMMY = "ON" ]; then
	echo "1. Run this script in dummy mode (nothing happens for real)"
	DUMMY="echo  -------------------------------"
fi

echo "2. Use $MY_EDITOR as the edior to use"
echo "3. Use $MY_DIRECTORY as the install directory to run this script from"

wait_for_user

}



admin
install_ubuntu
start_on_new_box
install_xfce
install_nvidia
change_sources_file
install_personal_stuff
install_ivtv
setup_ivtv
final_words


And the new sources.list file

> 

#This is the sources.list file. Save it in the same directory as the one above

deb cdrom:[Xubuntu 6.06 _Dapper Drake_ - Release i386 (20060601)]/ dapper main restricted

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

####################   mythtv   ######################
deb [http://www.hellion.org.uk/debian](http://www.hellion.org.uk/debian) sid main
deb-src [http://www.hellion.org.uk/debian](http://www.hellion.org.uk/debian) sid main

###Best one I can find for Dapper and myth 0.19###

deb [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main
deb-src [http://home.eng.iastate.edu/~superm1](http://home.eng.iastate.edu/~superm1) dapper main

######################################################

#deb [http://knm.org/mythdebs/](http://knm.org/mythdebs/) binary/
#deb-src [http://knm.org/mythdebs/](http://knm.org/mythdebs/) source/
#deb [http://deb.thehunter.ws/](http://deb.thehunter.ws/) breezy mythtv-stable
#deb-src [http://deb.thehunter.ws/](http://deb.thehunter.ws/) breezy mythtv-stable



Please join in and help with this.
I will edit the post as I get it working better and better. ):

Bye H:p

---

### Post by kombipom on 2006-06-13
This is a great idea, I'm just waiting for my TV card to arrive before I enter the Myth install & configure maze.  If you can get this working smoothly it will be a massive help (to a lot of people).  As I'm getting a Hauppage DVB-T 500 I won't need the ivtv bit right?  Whatever happens I'll let you know and try to help if I can.

---

### Post by HJB on 2006-06-13
[QUOTE=kombipom]This is a great idea, I'm just waiting for my TV card to arrive before I enter the Myth install & configure maze.  If you can get this working smoothly it will be a massive help (to a lot of people).  As I'm getting a Hauppage DVB-T 500 I won't need the ivtv bit right?  Whatever happens I'll let you know and try to help if I can.[/QUOTE]

mmm, You do need the IVTV stuff. Look here
"...Hauppauge PVR 150/500

This card has an hardware encoder (but no hardware decoder and no tv out) and is *newly* supported by ivtv. As the card has an v4l2 interface like the other cards, it is also supported by analogv plugin. As this card does not have the hardware MPEG decoder and no TV out you can use this card like a Budget DVB card only as DVB input device, for TV out and OSD you need an additional output device. But please note: these card needs the *newest ivtv drivers* you can get, at least 0.3.8

The PVR 500 is the combination of two 150er on one printed circuit board..."
[http://www.linuxtv.org/vdrwiki/index.php/HauppaugePVR#Hauppauge_PVR_150.2F500](http://www.linuxtv.org/vdrwiki/index.php/HauppaugePVR#Hauppauge_PVR_150.2F500)

and here

"... Hardware Encoder cards

    * iTVC15 family of MPEG encoders supported by the IVTV drivers
          o Hauppauge PVR-500
          o Hauppauge PVR-350 (TV-Out function works, but is not recommended, see details on this page)
          o Hauppauge PVR-250
          o Hauppauge PVR-150
          o AVerMedia M179 
    * Matrox Marvel G200/G400 MJPEG encoders..."

[http://www.mythtv.org/wiki/index.php/Video_capture_card](http://www.mythtv.org/wiki/index.php/Video_capture_card)

and here

"... Technical Background

The guide above shows you how to install all of the firmware files, even though all of them are not needed given a particular PVR-xxx card. There is no harm in installing all of the firmware files; the unneeded ones will just never be loaded.

The v4l-cx2341x-dec.fw firmware and v4l-cx2341x-init.mpg (named v4l-cx2341x-init-mpeg.bin in 0.4.1 and earlier) are needed for the PVR-350 only. Also, v4l-cx2341x-init.mpg is not really a firmware file, but a very small endian-flipped MPEG file needed to initialize the mpeg decoder so that the YUV playback (not the framebuffer) works.

The v4l-cx25840.fw firmware is only needed for cards with a cx2584x chip, currently only the PVR150, PVR500 and Yuan PG600/Diamond PVR-550 cards..."

[http://ivtvdriver.org/index.php/Firmware](http://ivtvdriver.org/index.php/Firmware)

Hope this helps.

Bye
H

---

### Post by kombipom on 2006-06-14
Sorry I didn't give the real name, it's a Nova-T 500 not a PVR 500.  Others have said that they have it working with Myth so I'm hopefull.  It had better work, the wife wants some return on all the money I've been spending recently :razz:

And why do some of the cards have TV out? Won't the TV signal come from the graphics card?  Sorry if I am being monstrously dumb.

---

### Post by HePe on 2006-06-14
Thank you for your work!

I've got a little trouble with the sources.list. Dapper reports malformatet lines. What ist wrong?

Another trouble is, that the "dec" firmware or driver does not work till now. The IVTV reports the error -12.

```
[4294699.140000] Linux video capture interface: v1.00
[4294699.234000] ivtv: no version for "struct_module" found: kernel tainted.
[4294699.239000] ivtv:  ==================== START INIT IVTV ====================
[4294699.239000] ivtv:  version 0.4.5 (tagged release) loading
[4294699.239000] ivtv:  Linux version: 2.6.15-23-386 preempt 486 gcc-4.0
[4294699.239000] ivtv:  In case of problems please include the debug info between
[4294699.239000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[4294699.239000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[4294699.305000] logips2pp: Detected unknown logitech mouse model 99
[4294699.381000] input: ImExPS/2 Logitech Explorer Mouse as /class/input/input2
[4294699.529000] Floppy drive(s): fd0 is 1.44M
[4294699.543000] FDC 0 is a post-1991 82077
[4294699.624000] ivtv0: Autodetected WinTV PVR 350 card (cx23415 based)
[4294699.624000] **** SET: Misaligned resource pointer: d22d29e2 Type 07 Len 0
[4294699.625000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[4294699.625000] PCI: setting IRQ 5 as level-triggered
[4294699.625000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[4294699.625000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[4294699.706000] tveeprom: ivtv version
[4294699.706000] tveeprom: Hauppauge: model = 48134, rev = J321, serial# = 7197112
[4294699.706000] tveeprom: tuner = Philips FM1216 (idx = 21, type = 5)
[4294699.706000] tveeprom: tuner fmt = PAL(B/G) (eeprom = 0x04, v4l2 = 0x00000007)
[4294699.706000] tveeprom: audio processor = MSP4418 (type = 19)
[4294699.706000] tveeprom: decoder processor = SAA7115 (type = 13)
[4294699.706000] ivtv0: i2c attach to card #0 ok [client=tveeprom, addr=50]
[4294699.735000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[4294699.735000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[4294699.897000] saa7115 1-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[4294700.002000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[4294700.073000] saa7127 1-0044: ivtv driver
[4294700.075000] saa7127 1-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
[4294700.075000] ivtv0: i2c attach to card #0 ok [client=saa7127, addr=44]
[4294700.143000] msp3400 1-0040: chip=MSP4418G-A2 +nicam +simple +simpler +radio mode=simpler
[4294700.144000] msp3400 1-0040: msp34xxg daemon started
[4294700.160000] ivtv0: i2c attach to card #0 ok [client=MSP4418G-A2, addr=40]
[4294701.050000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294701.059000] ivtv0: unable to open firmware v4l-cx2341x-dec.fw
[4294701.059000] ivtv0: did you put the firmware in the hotplug firmware directory?
[4294701.059000] ivtv0 warning: failed loading decoder firmware
[4294701.059000] ivtv0 warning: Error loading firmware -1!
[4294701.059000] ivtv0: Error -1 initializing firmware.
[4294701.074000] ivtv0: Error -12 on initialization
[4294701.074000] ivtv: probe of 0000:00:09.0 failed with error -12
[4294701.074000] ivtv:  ====================  END INIT IVTV  ====================

```

what do I wrong?

If you like to - I will test your script ;-) and report to you, till my VDR or Myth runs ;-)

After changing the sources.list .... it worked quite better. But my Problem ist still here:

```
[4294701.050000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[4294701.059000] ivtv0: unable to open firmware v4l-cx2341x-dec.fw
[4294701.059000] ivtv0: did you put the firmware in the hotplug firmware directo ry?
[4294701.059000] ivtv0 warning: failed loading decoder firmware
[4294701.059000] ivtv0 warning: Error loading firmware -1!
[4294701.059000] ivtv0: Error -1 initializing firmware.
[4294701.074000] ivtv0: Error -12 on initialization
[4294701.074000] ivtv: probe of 0000:00:09.0 failed with error -12
[4294701.074000] ivtv:  ====================  END INIT IVTV  =================== 
```

---

### Post by HJB on 2006-06-15
Hello HePe

Is this a new install or over a current box?
did you run the script?

I got that problem initially when I followed another howto and it came down to the files going into the wrong directory,
You'll see in the script I use
sudo tar zxvf firmware.tar.gz -C /lib/firmware/

do a locate and see where the files went.

Also have a look here [http://ivtvdriver.org/index.php/Howto:Ubuntu](http://ivtvdriver.org/index.php/Howto:Ubuntu)
The say "the firmware package creation script /usr/bin/ivtv-makefwpkg (from the ivtv0.4-utils package) doesn't work with Ubuntu"

Thats why I did it as in the script.

What hardware do you have?

Bye
H

---

### Post by HePe on 2006-06-15
> Is this a new install or over a current box?
did you run the script?

It was a new install - with many tries ;-)

Yes I did run the Script.

And now I tested it with an initial Installation of the Dapper Desktop. The sources.list gives me an error in line 6. When I solve it, then line ... The system tells me about parse-error. 
Thats, because the sources.list in your package have url-tags around the locations. This is corrected very easily ;-)

The installation of xfce did not work out of the script in my case ... Would it be a good idea to start this **after **changing the repopsitories?

> What hardware do you have?

Athlon 800 with Hauppauge PVR-350

---

### Post by qrazi on 2006-06-18
The parse error, i got it too. It was caused because the repositories in the sources.list file had url /url hooks around them. I mannually deleted them, and then the update of apt-get went fine, altough it gave a report that there is no public key for the hellios repositorie. I fixed that by doing:

wget [http://www.hellion.org.uk/public_key.asc](http://www.hellion.org.uk/public_key.asc)

followed by:

sudo apt-key add public_key.asc

However, after the script asks if i want to install Mythtv 0.19, and i type Continue, nothing happens. I just get back to the prompt in the console. Any idea about that?

/edit: i just actually read the script... i am no script writer, but i guess there is no line in the script for actually downloading and installing the myth 0.19 packages is there? so i can just do that by using synaptic and install all the 0.19 packages?

/edit2: I used synaptic to install the 0.19 mythtv packages. Mythtv actually work again now. It still recognized my old recordings, and as far as i can see, my mythconverg database is also being used.

But, mythmusic, myth video, mythweb and more are gone. And i cannot install them trough synaptic.

Right now i am trying if using Hyams guide to upgrading to 0.19 works ([http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html) chapter 9.8)

---

### Post by kraz on 2006-06-24
Great idea.

I dont know much of scripting and stuff, but will gladly put my system to test for this...

I will report back in, later on.

Nice work.

---

### Post by rothgar on 2006-08-10
I am curious if there have been any updates to this?

I would also like to know if the mythtv .19 sources you listed have mythtv compiled with XvMC flagged?  I think that is why I cannot watch live tv and I was told I would have to re compile.  This may be something to check out if I am going to have to start over anyway.

---

### Post by nzruss on 2006-08-13
> **rothgar said:**
> I am curious if there have been any updates to this?


I've been keeping an eye on this thread and it seems to have gone dead. I just cant get the script to work, and it breaks a whole bunch of stuff. 

I am too new to scripting to try and get it going the way I like, but i would have thought grabbing a few autodetect and auto-setup scripts from the Knoppmyth project would have been the way to go.

BTW, I have posted [my Mythtv Build here]("http://www.nzrussmyth.blogspot.com/")

---

### Post by HJB on 2006-08-15
HI guys. I started this thread but became so frustrated with the lack of official myth0.19 support at that time (repository) that I moved away from ubuntu and got my box up in gentoo. They have very great support there.
Sorry bout that.

I havn't recently looked in the ubuntu repositories so please tell me if there is anything 0.19 wise there.

My gentoo box runs like a charm
I have kububuntu still on my desktop so I haven't completely abandoned ububtu ):

Bye
H

---

### Post by mapleshade on 2006-08-24
> **HJB said:**
> HI guys. I started this thread but became so frustrated with the lack of official myth0.19 support at that time (repository) that I moved away from ubuntu and got my box up in gentoo. They have very great support there.
Sorry bout that.

I havn't recently looked in the ubuntu repositories so please tell me if there is anything 0.19 wise there.

My gentoo box runs like a charm
I have kububuntu still on my desktop so I haven't completely abandoned ububtu ):

Bye
H

So, the perfect MythTV install for Dapper is using a different OS.  Perfect.  HJB, can you post a good link for a Gentoo install?
I use several variations of Ubuntu with great success, but not with MythTV.

---

### Post by HJB on 2006-08-25
Hi there.
Here is the link
[http://gentoo-wiki.com/HOWTO_Setup_MythTV](http://gentoo-wiki.com/HOWTO_Setup_MythTV)

I really like gentoo for these type of things. It just works and the community is very helpfull.
Sorry guys

If I start to work on ubuntu and myth now, my wife will kill me....):

Bye H

---

### Post by arng on 2006-09-01
Hey Dude,

Such an installer is the right way to go.  It can ease installation for many folks.  It is true that one has to understand the steps and be able to googleshoot the problems.  But at least a simple level of automation can be a great boost.  I am sure that anyone technical who is installing myth keeps some install notes, so keeping it as a simple interactive script is just natural.

With a little more effort it should be able to be cross platform too.  You passing a platform is fine, but please take my 2 cent suggestion and keep on going no matter what the platform is.  This script should be added to the myth codebase and svn too.

Thanks for the efforts!

---

