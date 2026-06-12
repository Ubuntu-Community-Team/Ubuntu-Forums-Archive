---
title: "low-graphics mode after upgrade."
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by goli123 on 2011-10-15
hey, i hope this is the right place for my problem. i just upgraded my system to the new ubuntu version. i was asked to restart my computer, but then i got the folowing massege:

"**Ubuntu is running in low-graphics mode **
your screen, graphic card, and input device settings could not be detected correctly. you will need to configure these yourself."

after that i can choose one of the follwing
*run ubuntu in low-graphics mode for just one session - computer freezes
*reconfigure graphics - when i choose that i cant choose anything in the next menu.
*troublehoot the error - i can view some logs.
*exit to console login - console view.
*restart X - computer freezes

i tried to reconfigure xorg as in:
```
sudo /etc/X11/X -configure
```

and i got error messages:
*Number of created screens does not match number of detected devices
*Configuration faild.

 i hope you guys can help me with this.
thx, david.

---

### Post by 23dornot23d on 2011-10-15
Which graphics card do you have in your machine ?

---

### Post by goli123 on 2011-10-15
i'm not sure, its on board graphic card. 
my computer is a lenovo g550 with nitu1 motherboard.
when i try to use cpu-z i cant see gc name. any other way to see that? (im using hiren's tools to lanch the cpu-z).

---

### Post by 23dornot23d on 2011-10-15
type in a terminal (LSPCI) ...... lower case ..... letters

lspci

and post the results

---

### Post by goli123 on 2011-10-15
u need the all thing or just the display?
anyways the display part is this:

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

if you need ill type in the rest.

---

### Post by goli123 on 2011-10-15
anybody? i really need my computer up and running.

---

### Post by MAFoElffen on 2011-10-15
> **goli123 said:**
> anybody? i really need my computer up and running.
The work-around for that GPU in Ubuntu... Since you can start in Low-graphics mode, boot.

After boot, open a terminal session
```

gksudo /etc/default/grub

```Anywhere in that file, add a line to it saying
```
[FONT=monospace]
[/FONT]GRUB_GFXPAYLOAD_LINUX=text

```Save and exit.
```

sudo update-grub

```
Reboot and test (you may also need a vga= option, but we'll see.)

---

### Post by madjr on 2011-10-15
can you also send this error to launchpad from your 11.10 install so the developers can be aware of the problem.

in a terminal please type and follow the simple instructions:

```
ubuntu-bug unity
```

Thanks

ps. i honestly think these reports should be sent automatically when ever unity / upgrading fails.

---

### Post by goli123 on 2011-10-15
I typed ths command:

```
sudo dpkg --configure -a
```

and now i dont get the "Ubuntu is running in low-graphics mode" message anymore. but i'm stuck on boot at "checking battery state"
what can i do now?

---

### Post by MAFoElffen on 2011-10-15
> **goli123 said:**
> I typed ths command:

```
sudo dpkg --configure -a
```and now i dont get the "Ubuntu is running in low-graphics mode" message anymore. but i'm stuck on boot at "checking battery state"
what can i do now?
At that of the boot process it's starting X and looking for your graphics driver...

Did you add that line I suggested in your /etc/default/grub file?  If so, then also in that file, change
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
To 
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=792"

```
And change
```

#GRUB_GFXMODE=640x480

```
To 
```

GRUB_GFXMODE=1024x768

```
After saving run
```

sudo update-grub

```

---

### Post by goli123 on 2011-10-16
i did all the changes to the grub file. but i'm still stuck in the same "checking battery state"

anyother ideas?

---

### Post by madjr on 2011-10-16
> **goli123 said:**
> i did all the changes to the grub file. but i'm still stuck in the same "checking battery state"

anyother ideas?

check if you have these problems when running ubuntu from an usb stick or cd.

also it will let you use your computer, backup, etc. meanwhile.

---

### Post by goli123 on 2011-10-16
> **madjr said:**
> check if you have these problems when running ubuntu from an usb stick or cd.

also it will let you use your computer, backup, etc. meanwhile.

doesnt have this problems when using live cd. but still im hoping to get this system running without reinstalling..

---

### Post by goli123 on 2011-10-16
i really need your advice. do you think that i have any chance tto bring my system back to life again or should i start backing up everything now?

---

### Post by madjr on 2011-10-16
> **goli123 said:**
> i really need your advice. do you think that i have any chance tto bring my system back to life again or should i start backing up everything now?

you might try to bring it up to life, but am sure is going to take longer than backing up and reinstalling (probably in like 35 mins and you are done!).

Upgrades have an 50% chance to going bad for many reasons (specially on non LTS releases.). This is why every new release should be tested in another partition. If things go well just migrate and either keep the old one as backup or format it to gain space.

I always have at least 2 partitions: Main and testing.

Anyway am glad that the live-cd works as it should.

Cheers and let us know if you need further help.

---

### Post by MAFoElffen on 2011-10-16
> **madjr said:**
> you might try to bring it up to life, but am sure is going to take longer than backing up and reinstalling (probably in like 35 mins and you are done!).

Upgrades have an 50% chance to going bad for many reasons (specially on non LTS releases.). This is why every new release should be tested in another partition. If things go well just migrate and either keep the old one as backup or format it to gain space.

I always have at least 2 partitions: Main and testing.

Anyway am glad that the live-cd works as it should.

Cheers and let us know if you need further help.
Since the OP upgraded vs. a new install, then we don't know what he would lose from a new install. It would be easier than this post a question, time passes, he tries something... It doesn't work, and we take forever on what should be a few hours to a day... I'm patient.

I'll lay this out for all --> Basically, your Intel video chipset should work out-of-the-box with Ubuntu.  That is what Intel says about that chipset. It should work with X.orgs xorg-xserver-video-intel driver.  That is what starting and running the LiveCD confirms.  "Something" is there on your PC, telling it otherwise.

My recommendation from here? Something really basic. Try to return things to a default:

1.Edit the /etc/default/grub file to return it to close to default. 
 a. The "#" character is a comment character in grub files.
 b. Comment out the "GRUB_GFXMODE=1024x768" line by add a "#" and space before it...
 c. Comment out the "GRUB_GFXPAYLOAD_LINUX=text" line.
 d. Save and exit.
 e. Run "sudo update-grub"

2. While still in a terminal
```

sudo mv /etc/X11/xorg.conf xorg.conf.old

```

3. Reboot and try.  

*** Of course you could always alternately reinstall fresh with a new install... If so, I would export the packages installed and backup your home directory if you want to keep what you have now.

---

### Post by goli123 on 2011-10-16
i did all you suggested right now and i'm still stuck right after the battery test.

:(

---

### Post by MAFoElffen on 2011-10-16
> **goli123 said:**
> i did all you suggested right now and i'm still stuck right after the battery test.
If you boot on a LIveCD in the Live Image > If you cliick on your user_name in the top bae and select System Settings > Select Additional Drivers... Does it suggest any drivers for you?

While on the LiveCD, go to the Places Icon > Select the partition where your install is > Navigate to /var/log/xorg.0.log > Open it with text editor.  Post it here inside code tags.

In the same directory, do the same for your syslog and dmsg logs... Remeber to post all these logs inside openning and closing code tags.  If not, they will be miles long in a post.  

If you doun't know how, when you post > look up at the top toolbar > there will be an "#" icon in the toolbar. That is the code tags.  Cut and paste your text. Hhightlight that text and press the "#" icon.

There is just something there that we haven't seen yet.  Offhand, what would you lose if you did a clean install?  No 100% garrantee that this would get around this, but it might... Just curious.

---

### Post by goli123 on 2011-10-16
this logs takes a 18mb file. cant post it here.
anyways i started a fresh install so less relevent if you want the logs anyway just tell me how to tranfer it to you.

---

### Post by MAFoElffen on 2011-10-16
> **goli123 said:**
> this logs takes a 18mb file. cant post it here.
anyways i started a fresh install so less relevent if you want the logs anyway just tell me how to tranfer it to you.
Never mind-- a fresh install may take care of it anyways. (Hoping for you.)

Personally, I'm always open to a fresh install.  I do about 20 a week on 7 test boxes.

---

