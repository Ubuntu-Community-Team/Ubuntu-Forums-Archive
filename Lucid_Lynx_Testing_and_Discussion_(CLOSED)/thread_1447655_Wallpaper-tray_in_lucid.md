---
title: "Wallpaper-tray in lucid"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by .salo on 2010-04-05
Does anybody know why wallpaper-tray applet disappear from lucid repository? 

Does  it planed to return this applet back to repository?

---

### Post by seeker5528 on 2010-04-07
Can't really answer that, I expect it was probably due to lack of maintenance upstream.

Never got into any of the wallpaper changing things in recent times, but the questions did spark my interest again, which led me to wally, but I have not got it set up yet beyond creating a .dektop file in '~/.config/autostart' with contents:

```
[Desktop Entry]
Type=Application
Exec=/usr/bin/wally
```

So it would start when I log in.

Later, Seeker

---

### Post by autocrosser on 2010-04-07
It was not maintained at all upstream---you can still use the one from Karmic..I've had it work...If you are testing Gnome Shell you need to use the older .46 release...that one works also.

---

### Post by michaelzap on 2010-04-08
I was disappointed when I found that Wallpaper Tray was not available for Lucid. I now just use a Python script in my Startup Applications to rotate the background image. Thats all I really wanted to do anyway, so this works well enough for me.

The script is as follows:
```
#!/usr/bin/env python

import subprocess
import os
import sys
import time
import random

# The default wallpaper interval (pass -t seconds to override)
changetime = 1800.0
# The default wallpaper folder (must have only Gnome supported images)
imagefolder = "~/Documents/backgrounds/"


lastpicindex = 0

def get_pictures (folder):
	try:
		pictures = os.listdir (folder)
		return pictures

	except OSError:
		print "Folder " + folder + " not found."
		sys.exit ()

def change_curscreen (folder, pictures, type):
	# learn to use python :)
	if "random" != type:
		return 0

	picindex = lastpicindex
	while picindex == lastpicindex:
		picindex = random.randint (0, len (pictures) - 1)
	
	curpicture = pictures [picindex]
	
	command = 'gconftool-2 --set /desktop/gnome/background/picture_filename --type string "' + folder + curpicture + '"'
	subprocess.Popen (command, shell=True)

	print "changing screen to " + folder + curpicture
	time.sleep (changetime)

def start_screenchanger (folder):
	global changetime

	pictures = get_pictures (folder)
	change_curscreen (folder, pictures, "random");

def filter_foldername (folder):
	if not folder.endswith ('/'):
		folder += '/'

	command = "echo " + folder
	try:
		unixfilter = subprocess.Popen (command, stdout=subprocess.PIPE, shell=True)
		folder = unixfilter.communicate ()

	except OSError:	
		print folder
		print "Failed to launch unix echo command"
		sys.exit ()

	retfolder = folder[0].strip ('\n')
	return retfolder

def display_help ():
	print ""
	print "Simple background changer script 0.1"
	print "\t--help or -h\t\t\tDisplay this help message"
	print "\t--time or -t <seconds>\t\tWallpaper change interval in seconds"
	print ""

def main ():
	global changetime
	global imagefolder

	for i in xrange (0, len (sys.argv)):
		if sys.argv [i] == "--time" or sys.argv [i] == "-t":
			changetime = float (sys.argv [i + 1])
		elif sys.argv [i] == "-h" or sys.argv [i] == "--help" or sys.argv [i] == "-help":
			display_help ()
			sys.exit ()

	imagefolder = filter_foldername (imagefolder)

	while (1):
		start_screenchanger (imagefolder)

main ()
```

EDIT: I don't remember where I found this or I'd give credit to the author...

---

### Post by .salo on 2010-04-12
Wallpaper-try give a capability to delete current wallpaper from file system.

---

### Post by shane2peru on 2010-04-13
I miss wallpaper-tray!  Perhaps I will give the python trick a go.  Does anyone else have any replacements besides that?  I really loved the rotating wallpaper and ability to remove ones I didn't like.  Something in the repos?  I tried drapes before, and it didn't work well, or something was wrong with it, perhaps I will have to give that another try.

Shane

---

### Post by setherd on 2010-04-13
even drapes is broken for me, I miss wallpaper-tray!

---

### Post by autocrosser on 2010-04-13
You can use the one from Karmic--it works....Goto: [http://archive.ubuntu.com/ubuntu/pool/universe/w/wallpaper-tray/](http://archive.ubuntu.com/ubuntu/pool/universe/w/wallpaper-tray/)  & get the 0.5.5 version that works for you & then have gdebi install it.

---

### Post by shane2peru on 2010-04-14
There is also gbackground, which works, however needs some kind of help so that it will startup on it's own without reconfiguring it on every startup.  I also found wally, however it is kde dependent, pulling in a lot of extra dependencies.

Shane

---

### Post by .salo on 2010-04-27
Two day left and nothing.  Sad ...
Is there a way to make old version (for Karmic) work in Lucid?

---

### Post by rbolio on 2010-04-27
How can we run gbackground to start from startup w/o reconfiguring?

---

### Post by autocrosser on 2010-04-28
> **.salo said:**
> Two day left and nothing.  Sad ...
Is there a way to make old version (for Karmic) work in Lucid?

I posted that info slightly above your post--use the download link & then have gdebi install it...I'm using it right now.

---

