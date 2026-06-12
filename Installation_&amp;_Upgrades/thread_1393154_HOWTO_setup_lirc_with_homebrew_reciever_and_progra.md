---
title: "HOWTO setup lirc with homebrew reciever and program your keybindings...UPDATED"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by swingboy3 on 2010-01-29
[B]#1 My setup and hardware
[/B]
Thanks to member encompass I got my LIRC HOMEBREW transmitter(blaster) and receiver working in my ubuntu system.  This is an updated post to help those who may be having similar problems as I did and also to update it to KARMIC KOALA.  You ccan find the original post [here.]("http://ubuntuforums.org/showthread.php?t=163496")

I will try to take you step by step through my installation process as best I can remember noting the mistakes that I made.

I started with a clean install of mythbuntu 9.10 with mythtv 0.22.  I disregarded all of the mythtv pre-configured stuff just so you all know.

I used a homebrew transceiver that is really simple to make if you have any soldering experience at all.  It is also really cheap to make if you have access to some kind of electrical stockroom or electronics store.  The basic plans are [here]("http://www.lirc.org/receivers.html") for the transmitter and [here]("http://www.lirc.org/transmitters.html") for the receiver.  Another note on this is that you can have both transmitter and receiver on the same serial port.  In fact I don't know if you can do it any other way.  In addition I used the simplest diagrams that were available.  If you want multiple IR blasters (transmitters) you probably need an amplifier of some kind as they describe.

You can also buy the IR transceivers on ebay and what not.  They are not expensive as well, but not as fun to make.

_________________________________________________________________

**#2 Installing LIRC Software and testing hardware**

First start by finding out what kernel version you have.  Open a terminal and type:

> uname -r
Mine spit out 2.6.31-17-generic.  All you care about is the 2.6.31 so when you see me type 2.6.31 replace it with the data you had there

Next we will remove LIRC if you already have it installed.
> sudo apt-get remove lirc
sudo apt-get install linux-source-2.6.31 build-essential
cd /usr/src/
sudo tar xvf linux-source-2.6.31.tar.bz2
sudo ln -s /usr/src/linux-source-2.6.31 /usr/src/linux
cd /usr/src/linux
sudo make oldconfig
sudo make menuconfig 
If you get an error at this point you need to install the ncurses library like this
> sudo apt-get install libncurses5-dev
Now thatthis is done we can continue installing like this:
> 
sudo make include/linux/version.h
sudo make modules
sudo touch /usr/src/linux/Rules.make 
Just a warning that "sudo make modules" takes a long time to compile.  Go ahead and go to dinner or let it run overnight.  It takes for stinkin' ever.

Now open a web-browser and navigate to [http://www.lirc.org/]("http://www.lirc.org/")  Download the latest version of the lirc build.  It should look something like "lirc-0.8.6.tar.bz2"

Ok back to your terminal window and navigate to...
> cd /usr/src/linux/
sudo mv /home/uname/Downloads/lirc.0.8.6.tar.bz2 /usr/src/linux/
sudo tar -xvf lirc-0.8.6.tar.bz2 

After this gets done it will create a new folder called lirc-0.8.6/  Navigate into this folder by
> cd lirc-0.8.6/

Now we can start to build this bad boy
> sudo ./setup.sh 
If this errors with a "Dialog not found" error you need to install dialog
> sudo apt-get install dialog

This will open up a couple of dialogs 
[DIALOG 1]("http://img162.imageshack.us/i/lircsetup1hq.png/")
[DIOLOG2]("http://img161.imageshack.us/i/choice8oq.png/")
I simply kept the default settings. and selected value #3 on DIALOG1 to "SAVE configuration & run configure"
If you don't select this option you still need to run ./configure before you continue
Now make and make install as follows
> sudo make
sudo make install
Once this gets done being made it is time to tell LIRC where the device is.  This is assumed that you are using serial port 0.
<--/dev/ttyS0 is com port 1 so if you need com 2 use ttyS1...-->  
> setserial /dev/ttyS0 uart none
sudo depmod -a
sudo modprobe lirc_serial
sudo modprobe lirc_dev 
You should get a /dev/lirc0. That is your lirc device!

If you have gotten this far with no major errors you are doing well.  

This next step is just to see if this works at all.
> sudo mode2
What this does is starts spitting out the raw values that the IR receiver gets.  There is always a bit of IR noise in the room so you should get some random numbers.  Now take any IR remote and point it at the receiver.  If it worked you should see the numbers kind of synchronize over the period that you hold the button.  Now is the time to celebrate because the darn thing works, from here on it is just a matter of messing around with it.

________________________________________________________________

**#3  Make Changes permanent**


So what we did above is just temporary.  In order to make this permanent we will make a file to be run at startup.

So just do the following.  Go to your home directory
> cd /home/uname/
sudo nano homebrew
This should open up a blank text document called "homebrew"   you can call this anything you want, but I am copying member encompass' notation just to keep with what he did.
Then past into it the following
> #! /bin/sh
# /etc/init.d/homebrew: Loading the Homebrew IR receiver (IT'S ALIVE!).
setserial /dev/ttyS0 uart none
modprobe lirc_serial
modprobe lirc_dev
sleep 1
ln /dev/lirc0 /dev/lirc
lircd
irexec --daemon

Now modify the permissions of this file and move it
> sudo chmod +x homebrew
sudo mv homebrew /etc/init.d/
sudo ln -s /etc/init.d/homebrew /etc/rcS.d/S99homebrew 

Now reboot and see if everything works by typing the following
> sudo mode2
If this fails check the following.  For some reason in my release the folder /var/run/lirc was missing after reboot.  Check to see if this folder exists.  If it does not you need to add one more line to /etc/init.d/homebrew by the following
> sudo nano /etc/init.d/homebrew
and add the this line before the "lircd" command
> mkdir /var/run/lirc

_________________________________________________________________

**#4 Setting a specific remote to your Receiver (make lircd.conf)**

This next section is to designed to connect key presses on your remote to commands in different programs.  What is really cool about this is you can program the keys to do things from controlling programs like mythtv mplayer xine, or you can run programs from the command line.  
In order to do this stuff first you need to either record your remotes buttons to a config file or find a pre-made config file for your specific remote.  You can find some pre-made config files [here.]("http://lirc.sourceforge.net/remotes/")

If you can't find your config file here is what you do.  Go to your home directory
> sudo /home/uname/
and run the following command
> sudo irrecord remote_name
where "remote_name" is a name you pick for your device.  I called mine insignia_TV1 because I felt like it so I ran
> sudo irrecord insignia_TV1
This program is a bit clunky so be patient with it.  It will ask you to name keys.  It has a list of approved names that will work.  I like to stick with the list for consistencies sake.  An example is "KEY_POWER" for power button.  If you want to see the available key names type "irrecord -l"

I really tried to avoid doing any raw-mode IR recording so I don't know how well that stuff works.  I tried to make sure that my remotes were recognized properly.  This takes some patients with this program so good luck.

So the file I produced was called insignia_TV1 and I moved this to where the config file goes by:...
> sudo cp /home/uname/insignia_TV1 /etc/lirc/lircd.conf


Now you can restart lirc by doing the following:
> sudo killall lircd
sudo lircd

Now we see if this works.  The "irw" command will translate the recorded remote commands received into the name of the remote and the name of the key pressed.  In the terminal type:
> irw
Now point your remote at the receiver and press one of the programmed buttons.  If it spits out your remote and the key pressed you are in business.

_________________________________________________________________

**#5 Mapping keys to computer functions (the .lircrc file)**

Now that you have this working all you need to do is map the key presses to programs and functions.  You could do this manually, but let's use a little trick.  This is done by making the lircrc file.  Luckily there is a little program that will do almost everything for you.  I don't know if this works outside of mythbuntu but I think it will.  Install this program:
> sudo apt-get install mythbuntu-lirc-generator
sudo mythbuntu-lircrc-generator
This creates a few files in /home/uname/ called .lircrc and also /home/uname/.lirc/mythtv etc.

If you open up .lircrc it just shows dependencies on the files in /home/uname/.lirc/mythtv  Now open up mythtv.  The generator auto-fills the keys to the best fit function in mythtv xine etc.  and they look like this:
> begin
    remote = insignia_TV1
    prog = xine
    button = KEY_ENTER
    config = EventSelect
    repeat = 0
    delay = 0
end


remote = designates which remote file it will use.  /etc/lirc/lircd.conf can contain as many remote files as you want as long as they have different names.

prog =  designates which program will be doing this.  There are lots of options and I will talk about executing bash commands or scripts using this one

button = designates the name of the button on that remote that executes this command

config = designates what command to execute in the specific program

repeat = is the number of repeated signals it will take to execute the command 0 means an infinite number of commands

delay = is the time lag.  I don't use this, so I don't know if this is in seconds or miliseconds.

Play around with this a bit.  Every time you edit these files you have to restart lircd and they should be applied.  What's more fun is you can start up one of these programs and control it from the comfort of your bed or couch or bunker.

_________________________________________________________________

**#6  Making button push turn into a bash command/script**

irexec

Remember how I said you could execute a bash command?  Well you can do it pretty simply by just adding a new button command to your .lircrc file.  Let's do something simple first.  Add this to the end of .lircrc

> begin
    remote = insignia_TV1
    prog = irexec
    button = KEY_ENTER
    config = gedit /home/uname/.lircrc &
    repeat = 0
    delay = 0
end


This comes under the assumption that you have gedit installed if not "sudo apt-get install gedit"

So at this point reboot and see if it all comes up.  Then press the button associated with this command.  It should pull up a GUI editor with the .lircrc file in it.  

One thing I have to say is that I'm not sure how to restart the irexec command.  Every time I updated a command for irexec I had to reboot, although you may be able to do this more easily another way.  Just a note that in the "hombrew" init file we initialized it by the command irexec --daemon

Obviously at this point you can replace the command with anything you can do in bash although I think you'd want to do something that does not need SU privileges.

__________________________________________________________________

**#7  IR blaster (transmitter) testing and usage**

The IR blaster or transmitter is a cool device that allows you to control most any IR receiving device such as your VCR or stereo.  The command is very simple and is documented [here.]("http://www.lirc.org/html/irsend.html")

Just to test it out open a terminal and type:
> irsend SEND_ONCE insignia_TV1 KEY_POWER

This command is consistent with what I have above so you change "insignia_TV1" and "KEY_POWER" to match what is in your /etc/lirc/lircd.conf file.

This should turn on/off that device.

If you want to test whether your blaster is working or not you can open up another terminal at the same time and type

> irw

point the blaster at the receiver and then open your original terminal and type

> irsend SEND_START insignia_TV1 KEY_POWER

Your second terminal should go crazy spitting out heaps of data.

Obviously you can use this command in an irexec fashion and be able to control multiple devices with one remote that they weren't even designed for.

_________________________________________________________________

**#8  Using your transceiver as a repeater**

Using your transceiver as a repeater can be tricky.  The idea here is that you transmit a signal to the receiver which it reads and then tells the irblaster to do something.  This is useful if you want to turn on everything at once or have some difficult remotes that aren't easy to find on a universal remote.

Here is the main physical aspect you have to be aware of.  If you hold the button on the remote just a fraction of a second too long the IR signals of the blaster and your remote overlap one another and do nothing or are very sporadic.  The solution is to delay your ir blaster by about 0.2 seconds. Here is how I did it.

First I made a script for the irblaster called my_irblast like this:
> sudo nano /usr/bin/my_irblast
and put this code in the text area
> #!/bin/sh
sleep 0.2
irsend SEND_ONCE $1 $2


I then added another command to my .lircrc file that looks like this
> begin
    remote = REMOTE_RX
    prog = irexec
    button = KEY_1
    config = /usr/bin/bh_remote_repeater REMOTE_TX KEY_1
    repeat = 0
    delay = 0
end


This doesn't allow for holding down buttons, but it does make this mess a lot easier.

_________________________________________________________________

**#9 Final tips or tricks**

Be careful with your .lircrc file as it will execute every command tied to one button press.  You can use this to your advantage as well if you want to turn on three different devices with one key press.

My remote is an old RadioShack 4 in one.  The cool part about it is that it will record IR commands from other remotes so you can program them into the buttons.  This has become my universal remote.  I just program it with a random device and assign the keys to my programs for each device.

IR blaster LED's are extremely directional.  Make sure you have them pointed in the general direction of the ir receiver of your device.


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

That's it.  I'm definitely no expert at this, but I feel like I have learned enough to share this as much as I can.  Again I appreciate member ENCOMPASS for his original post and for the sections that I plagiarized some of the code and comments from. Thanks ENCOMPASS.  Feel free to ask questions.  I'd love to get stumped by them.

---

