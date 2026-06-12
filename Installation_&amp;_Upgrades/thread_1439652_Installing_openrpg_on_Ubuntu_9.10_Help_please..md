---
title: "Installing openrpg on Ubuntu 9.10 Help please."
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by Sabastian on 2010-03-26
Alright, well after installing OpenRPG with the typical Sudo apt-get install openrpg command I found that openrpg could not run. Or wouldn't the exact error terminal spit at me was this:

Rooting OpenRPG at: /usr/share/openrpg
[WARNING] Could not create approot file.
[WARNING] Automatic directory resolution not configured.
/usr/lib/python2.6/dist-packages/wx-2.6-gtk2-unicode/wxPython/lib/splashscreen.py:5: DeprecationWarning: \

#####################################################\
# THIS MODULE IS NOW DEPRECATED                      |
#                                                    |
# The core wx library now contains an implementation |
# of the 'real' wx.SpashScreen.                      |
#####################################################/


  import wx.lib.splashscreen
/usr/share/openrpg/orpg/orpg_windows.py:985: DeprecationWarning: wx.MaskColour is deprecated, use `wx.Mask` instead.
  mask = wxMaskColour( gif, mask_color )
Reading Gametree file: /home/vansabbith/.openrpg/tree.xml... done.
Parsing Gametree Nodes  . . done
[Errno 13] Permission denied: '/home/vansabbith/.openrpg/lastgood.xml'
Current image cache size is set at 32 images, using random purge.

Followed by a pop up reading the following:

                                 Corrupt Tree! 
 Your game tree is being regenerated. To 
 salvage a recent version of your gametree 
 exit OpenRPG and copy the lastgood.xml 
 file in your myfiles directory 
 to /home/vansabbith/.openrpg/tree.xml 
 in your myfiles directory. 
 lastgood.xml WILL BE OVERWRITTEN NEXT TIME YOU RUN OPENRPG.
 

 The corrupt tree part I know is something OpenRPG related, the trouble is according to the "Search for Files" app lastgood.xml does not exist.

So yeah, anyone out there know what I should do?

---

