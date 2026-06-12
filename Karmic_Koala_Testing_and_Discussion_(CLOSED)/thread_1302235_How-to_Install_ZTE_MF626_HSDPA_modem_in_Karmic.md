---
title: "How-to: Install ZTE MF626 HSDPA modem in Karmic"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Abdullahnz on 2009-10-26
This guide explains a very easy way to reconfigure your ZTE MF626 HSDPA modem to be plug and play in Ubuntu in just 6 simple steps.

I am writing this guide because most of the information available concerning this hardware is outdated. As Ubuntu has evolved (particularly with the inclusion of NetworkManager) previous methods posted in this forum featuring lengthy tedious terminal coding  are no longer necessary.

You will need a computer with hyperterminal (included with windows XP) to send AT commands to the modem. I'm sure there is a way to do this from Ubuntu - someone with more expertise can correct me here. For now just borrow your friend's XP netbook while he is looking the other way. Please note that Vista no longer includes hyperterminal - see _[COLOR=Blue][here]("http://www.windowsreference.com/windows-vista/alternatives-to-hyperterminal-in-vista/")[/COLOR]_ for information on alternatives.

1. Connect your ZTE MF626 to the USB port of your computer with hyperterminal on it. The modem will automatically install the appropriate drivers and launch the User Interface (UI).

2. Determine the COM port of the modem by inspecting the modem properties under **Modems** in the Device Manager (do not get confused with ZTE Dianostics Interface or others).

3. Close the UI and open hyperterminal (or equivalent) and connect to the appropriate COM port using these parameters:

Speed: 115200
Data bits: 8
Parity: None
Stop bits: 1
Flow Control: None

4. Input the following command (you may wish to turn on local echo so you can see what you are typing):

AT+ZCDRUN=8

You should receive the following back in confirmation:

Close autorun state result(0:FAIL 1:SUCCESS):1

5. Close the hyperterminal connection and unplug the modem. Your modem is now reconfigured to be plug and play in Ubuntu.

6. Connect you modem to your Ubuntu computer. In the NetworkManager Applet you should find the option to create a new mobile broadband connection. Do so with the  location and APN appropriate to you ISP.

You should now be able to connect successfully to the internet and your modem should function as a plug and play device in Ubuntu. This works by disabling the self installation and autorun features which would otherwise cause Ubuntu to detect the modem as a CD-ROM. If you wish to revert the modem to it's orginal settings to allow atomatic UI installation on windows PCs the command to do so is: AT+ZCDRUN=9 (administered by hyperterminal as above)

This might work in Jaunty also. If anyone tries it please let us know. 

Sources that aided me in figuring this out:
*http://www.zte.com.au/downloads/USB_Modem_Config_Procedure.pdf*[I]/
http://www.matt-barrett.com/2008/11/telstra-pre-paid-wireless-broadband-ubuntu/[/I]

I hope this was helpful. Feedback welcome.

---

### Post by pdc on 2009-10-27
thanks very much for this Abdullahnz: which phone company in NZ uses the ZTE MF626 HSDPA modem?

---

### Post by Unkuiri on 2009-10-27
Hi, thanks, it's easier...:)...but there's a way to do all this in ubuntu...:)...using gtkterm...a program in the repositories..but still have to use usbmodeswitch to switch to the modem mode and go to the directory /dev and see the "port" created its something like ttyUSBX (X is a number)...
then open gtkterm it creates the file .gtktermrc...close gtkterm...go edit .gtktermrc file using for example:
> gedit .gtktermrc
it must look like this (a number instead of the X):
> [default]
port	= /dev/ttyUSBX
speed	= 115200
bits	= 8
stopbits	= 1
parity	= none
flow	= none
wait_delay	= 0
wait_char	= -1
echo	= False
crlfauto	= False
font	= "Nimbus Mono L, 14"
term_transparency	= False
term_show_cursor	= True
term_rows	= 80
term_columns	= 25
term_visual_bell	= True
term_foreground_red	= 43253
term_foreground_blue	= 43253
term_foreground_green	= 43253
term_background_red	= 0
term_background_blue	= 0
term_background_green	= 0
term_background_saturation	= 0,500000

now open gtkterm and write the command as Abdullahnz said and enter...
I'm using Jaunty...
good luck :)

(Sorry, I don't like depending on another OS)

---

### Post by Abdullahnz on 2009-10-27
> **pdc said:**
> which phone company in NZ uses the ZTE MF626 HSDPA modem?

Actually I live in Indonesia presently. I bought the modem to use here.


> **Unkuiri said:**
> (Sorry, I don't like depending on another OS)

Yes, some of us are still shaking off those last few ties of dependence, heh.

I'll give those instructions a go. Thanks.

---

