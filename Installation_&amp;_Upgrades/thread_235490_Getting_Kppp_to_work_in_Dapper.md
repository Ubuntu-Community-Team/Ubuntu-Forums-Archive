---
title: "Getting Kppp to work in Dapper:"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by danrael on 2006-08-13
First off, my install of Dapper did not come with Kppp available at all, though it was listed.  First, check to see if you can install it from 'Applications>Add/Remove>Internet', which should list kppp and kppp logview.  Depending on your hardware, it may allow an install; otherwise it  will require a download/install via of an internet connection onto the computer Dapper is installed on.  

Secondly, this procedure assumes the use of a hardware modem, [as compared to a Windmodem, or "soft" modem]. It should also work with Winmodems, assuming the modem and drivers are installed correctly beforehand.  A hardware modem, such as the US Robotics model 5610 [aka USR 0726 or 3Com   2977] internal controlerless PCI modem, needs no drivers to work with Linux.  External hardware [serial] modems also work in similiar fashion.

First you will need to determine which port your modem is on.  Do this by typing:  

[COLOR="Blue"]sudo wvdialconf /etc/wvdial.conf[/COLOR]

in a terminal window [Applications>Accessories>Terminal].  Assuming success, and the modem port is reported, go on to the next step, taking note of the reported modem port.  After a string of data, you should see something like the following:

[COLOR="Blue"]
Found a modem on /dev/ttyS4.
Modem configuration written to /etc/wvdial.conf.
ttyS4<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"[/COLOR]

Now, you will need to establish a connection via pppconfig.  Following is the procedure taken from the Ubuntu ModemHowTo:

pppconfig & pon/poff

This is a command line based option to manage dialup connections. This makes it very flexible, but maybe not so straightforward to configure.
Collecting Information

You will need:

    * Your ISP's phone number
    * Your username and password on the ISP
    * The name of the modem device (/dev/...)

Setting up ppp:

   1.  Open a terminal (Applications > System Tools > Terminal) and type

        [COLOR="Blue"] sudo pppconfig[/COLOR]

   2.  You will be on the main menu. Choose 'Create a connection'.
   3.  Leave the name as 'provider', hit 'Ok'.
   4.  Select 'Dynamic Use dynamic DNS', hit 'Ok'.
   5.  Select 'PAP Peer Authentication Protocol', hit 'Ok'.
   6.  Enter your user name for the ISP, hit 'Ok'.
   7.  Enter your password for the ISP, hit 'Ok'.
   8.  Leave the speed at 115200 as recommended, hit 'Ok'.
   9.  Choose Tone or Pulse dialing, hit 'Ok'.
  10.  Enter the phone number to your ISP (do not use any dashes), hit      
       'Ok'.
  11.  You can try to have your modem detected automatically, but it did 
       not work for me, so just ignore and move to next step.
  12.  If the modem wasn't detected, it will ask you for the port your  
       modem is on. Enter the device name for your modem, hit 'Ok'.[ie; 
       manually edit the default port to the correctly detected port; eg;   
       ttyS1 to  ttyS4]
  13.  A summary screen will appear and give you the opportunity to make 
       changes if needed.
  14.  Choose 'Finished Write files and return to main menu.'.
  15.  Choose 'Quit Exit this utility'.
  16.  Exit the terminal window, type: [COLOR="Blue"]exit[/COLOR]


Open a terminal window and type:  [COLOR="Blue"]sudo pon[/COLOR]  which should cause the modem to dial and connect.  Additionally, you can add a dialer applet to your upper desktop panel by right clicking on the panel field and choosing 'Add to Panel', which will display a list of icons.  Select the red phone icon labeled 'Modem Monitor' under 'System & Hardware', then press 'Add', which will place the applet in your panel.  To use it, right click on the icon and choose 'Activate', which will dial and connect.

At this point, once connected, you can download and install Kppp by typing:

[COLOR="Blue"]sudo apt-get install kppp[/COLOR]

This will take awhile, so do it at a time when you can afford to stay connected for awhile;  the package is over 27 mb.  This will download and install Kppp completely, and place the Kppp application under 'Applications>Internet>Kppp'.

After configuring Kppp* and querying your modem, attempt to connect to the internet, first disconnecting from the previous session.  You may receive a message after the modem dials to the effect that:  'the kppp daemon has died'.  Go to the [COLOR="Blue"]/etc/ppp/peers/kppp-options[/COLOR] file and change the text from 'auth' to 'noauth'.  If it already reads 'noauth', but has the # character ahead of the text, remove the # character, and try connecting again.  You may then receive another message re:  bug reporting being turned on or off:  follow the prompts to turn it on, and try connecting again.  This should work.

You will find some very useful information for your modem and dialer configurations here:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

*The Kppp Handbook can be found here:

 [http://docs.kde.org/stable/en/kdenetwork/kppp/](http://docs.kde.org/stable/en/kdenetwork/kppp/)

If anyone spots any errors in this description, please feel free to make the necessary corrections.

Good Luck!:grin:

---

