---
title: "Karmic 9.10 Sound Control (beta)"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by markbuntu on 2009-10-02
This is about getting familiar with the basic sound controls in Karmic and making use of them. This is based on a clean stock install of 9.10 beta and assumes that all your sound hardware is basically working. Sorry, but this is not about no-sound troubleshooting or other hardware issues.

Ubuntu Karmic Koala 9.10 includes many changes to the sound scheme among them is the new gnome volume control has integrated a lot of the previously missing PulseAudio controls to make your life easier. It is based on Pulseaudio 0.9.18 which is a vast improvement over previous versions.

(if you are using Kubuntu 9.10 this is probably not going to help you much. I will try to get around to that sometime soon.)

The first thing to notice is the new speaker icon on the panel. As usual a left click will gain access to the volume control which you can also control with your multimedia keys. A right click will bring up a small box with a mute button and Sound Preferences. 

**Sound Preferences**
Right click on the panel volume control (the little speaker icon) and  select Sound Preferences. At the top of the box is a volume slider and mute button and below that a bunch of tabs. Sound Preferences is also available in System/Preferences/Sound

Sound Effects
The first tab is Sound Effects where you can select the sound effects and theme and adjust the volume or set them to mute. You can also select No sounds in the drop down box. I have not tried to add another sound theme

Hardware
The next tab is labeled hardware, this is where you set up your sound hardware devices for input and output. If you have a built in sound device, web cam, usb sound device, pci card, or HDMI capable graphics card these all should be listed here.  I have 6 of these myself.  To configure each device just click on it and then use the Profile: drop down box to select the input and output configuration you desire or you can just turn it off by selecting off. 

Input
Here you can adjust your microphone inputs for all you hardware. Just click on the device and adjust the slider. If it has more than one input you can select the one you want to adjust in the drop down box.

Output
Here is where you select which output device you want to use, just click the button. You can also adjust the volume and balance using the sliders.
.
Applications
This will show all your applications that are playing sound, adjust the application volume or mute it.

**Trying it Out**
OK, it's time to try this out. Leave the Sound Preferences box open to the Applications tab.

Go to Applications/Sound and Video/ and click on Rythmbox Music Player. To keep things simple select one of the radio stations by double clicking it. You should see a the progress bar filling up and the word buffering. Look in Sound Preferences. There is Rythmbox, yay!! Can you hear it?  If you can then you are all set. You can adjust the volume or mute it but let's turn it up. Click on the Output tab. if you have a usb headset etc, you can move your music to that device by just clicking the button.  This will also move your multimedia keys to that device or can adjust the volume with the sliders etc. If you cannot hear Rythmbox make sure that you have the proper device selected in Output and the proper output selected in the Hardware tab. You will not hear anything if you have Digital output selected and your speakers are connected to the analog outputs. 


**Recording**
Lets' try to record something from a microphone.
Go to the Input tab in Sound Preferences. Make sure that you have selected the device your microphone is plugged into and the volume is turned up all the way and not muted and you have the right Connector selected. The Input level bars will help you figure that out.  Once you have that figured out we can record something. Open Sound Recorder and click the red button. You are now recording so quick, say something. Click the square box to stop recording and then push the green triangle to play back. did it work? If it did you are all set. If not then read on.

**Gnome ALSA Mixer**
If you want more fine grained control over your hardware or you are having some trouble with recording then you should get the Gnome ALSA Mixer which is in the Sound and Video Section of the Ubuntu Software Center which is at the bottom of the Applications menu.
The Gnome ALSA Mixer has one tab for each of your hardware devices. For each device you can go to Edit/Sound Card properties and select which items you want to appear in the panel so you can control them. Some devices have a lot of items and some only a few.  You can adjust the volumes of your inputs and outputs and mute them, select the IEC598 output and choose the input sources and set the capture and mic boost levels which are important for recording. Some of these things are also controlled by the panel volume control but some are not so the Gnome ALSA Mixer is a handy thing to have.


**The PulseAudio Controls**
If you want to be able to record what is playing in your speakers or have your music play on all your devices at the same time you need the Pulse Audio Controls. You can get these from the Ubuntu Software Center/Sound and Video. If you select the Pulse Audio Device Chooser it will install the rest automatically and they will appear in Applications/Sound and Video. Click on the Pulse Audio Device Chooser. This will put a little audio jack icon on your panel. Left click on it and choose preferences and check the box Start Applet on session login if you want it to stay there when you reboot. 

Simultaneous Output
If you want your sound to play on all your devices simultaneously then click in the PA device chooser and select Configure Local Sound Server. In the Simultaneous Output tab check the box then close it. Click the pa device chooser again and select Volume Control. Click the Output Devices tab and in the box at the bottom select All Output Devices, You should now have a device named Simultaneous Output to..........If you click on the little green button you will make it the default fall back output device, If you have Rythmbox playing it will  be in the Playback tab. At the right side is a box that shows the playback device click on that and change it to Simultaneous Output....... 

Recording what is playing in the Speakers
Now that you have the Pulse Audio Controls this is easy. Open the Pulse Audio Volume Control from pa device chooser. Click the Input Devices tab. At the bottom click the box nest to Show: and select All Input Devices.  Now, along with all the hardware input devices there are Monitors for them that will give you access to their outputs. To set the default device to one of the Monitors click on the green icon.  To test this open Sound recorder and, with something playing through the device you selected the monitor for click record and record a few seconds. Now play it back. Viola!!

There, that was not so hard was it?

**A few things you should know.** 
Simultaneous Output can use a lot of system resources at first especially if it is trying to output to more than two or three devices so if the sound starts skipping turn off the simultaneous output  and try turning some of the devices off from the panel volume control/hardware and try again.
The various volume controls can crash or freeze up if you have  more than one open at the same time so try to avoid that. They also control a lot of the same things so it is easy to make unintended changes. Tread carefully and try to remember how you went about things.
If you don't need to do the things that require the Pulse Audio Controls you would be better off to not install them.


Well there you go, basic sound control. If you have any questions, comments, or problems about any of this please do not hesitate to post.

regards,
mark

---

