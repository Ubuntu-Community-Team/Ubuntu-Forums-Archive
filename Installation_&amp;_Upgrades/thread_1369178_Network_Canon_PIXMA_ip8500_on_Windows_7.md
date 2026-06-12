---
title: "Network Canon PIXMA ip8500 on Windows 7"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by donovanjc on 2009-12-31
I had a home network with a Canon PIXMA ip8500 color inkjet printer connected to my wife's computer.  I just purchased a new computer with Windows 7 Home Premium 64-bit operating system.  I could not get the networked PIXMA ip8500 working from my Windows 7 computer.  After an hour and a half on the phone with Canon Support, I want to share the solution that worked.  There may be some extra steps along the way in my description because we tried so many things, but here is what worked.  For the sake of example, my computer name will be MY_COMPUTER, my wife's computer name will be WIFES_COMPUTER.

1)  Connected the Canon PIXMA ip8500 to MY_COMPUTER.  It was recognized by Windows 7, drivers were automatically loaded, and the printer could print a Test Page.
2)  Connected the Canon PIXMA ip8500 to WIFES_COMPUTER.  I made sure Printer Sharing was on, and the shared name set to CANON_PIXMA_ip8500.
3)  From MY_COMPUTER did START then Devices and Printers, and right clicked on the CANON PIXMA ip8500 icon that was installed when I had attached the ip8500 to MY_COMPUTER.
4)  Selected "Printer Properties" - not "Properties" at the bottom of the drop down list, but "Printer Properties" halfway down the list.
5)  Clicked on the "Ports" tab.
6)  Clicked at the bottom on "Add Port..."
7)  Double-Clicked on "Local Port" (or highlighted "Local Port" and clicked at the bottom on "New Port...").
8 )  In the "Enter a port name:" box, entered the following:
     \\WIFES_COMPUTER\CANON_PIXMA_ip8500
     followed by clicking the "OK" button.
9)  After OK-ing or Applying (I don't remember which and I don't want to delete what I did to test this part of the instructions), I went from the "Ports" tab to the "General" tab and did a "Print Test Page" and it worked.

I hope the results of two days of frustration plus a 90 minute call to Canon saves someone else a lot of time and frustration.

John Donovan
Garden City, NY

---

### Post by marnes on 2011-10-05
Thumbs up, this worked for me but I had to adjust the steps on my end.

I reversed the perspective as the printer is hooked up to my primary computer and I wanted the laptop to be able to access it as well, using Windows 7.

In my first attempt prior to googling a fix and coming here, I had set up the HomeGroup with printer sharing enabled, and the laptop was indeed able to discover the printer while attempting to add it. But it failed to connect. So then I followed these steps.

A couple differences: 

[LIST=1]
[*]I had 2 copies of the printer showing up in the laptop's printer list. One had the ports section greyed out. The other did not... so I used that one.
[*]The directory above did not work. I ended up using \\MYPCNAME\Canon Inkjet PIXMA ip8500. A good way to test this is to use the remote computer to confirm you can see it by typing in explorer: \\MYPCNAME so you can see the printer, then type in exactly what you see for the printer's display name including spaces, no quotes necessary. If you can confirm it, it will work. If you don't know what your PC name is, click the start menu, right click "My Computer" and go to properties. It will display the "Computer Name". That's what you want to use.
[/LIST]
 
Thanks for saving me a bunch of time on this!

---

