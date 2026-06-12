---
title: "msttcorefonts errant license response SOLVED"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by Billsey on 2011-02-05
Over the last week or so I ran into a problem that was caused by a mix of justifiable frustration with an Ubuntu distribution upgrade in combination with, well let's just be blunt about it: a dimly lit candle upstairs. ;-)


Ubuntu decided that it was going to download 50 megabytes of font packages whether I wanted it to or not, so, when I came back to find the license requester waiting for my response, I thought it was referring to those fonts that I told it not to download, but which it downloaded anyway (steam, steam, steam!), so I rejected the license. Instead, it was referring to the MScoreFonts package (which I DID want). Upon discovering what I had done, I found out that, using the Software Center, I could download those packages all I wanted to and they would NEVER install properly because I would never again get re-presented with the option of accepting the license. Instead, I am simply reminded over and over again that I have rejected the license. :( Apparently, Software Center is a tad unforgiving of stupid mistakes. :D

The answer, my friends, is not blowing in the wind, but is contained in a readme file that gets left where the fonts would have been installed.

To save you a little bit of time, here is what you need to do to get those fonts installed:

Open a terminal and enter the following quoted command (without the quotes, of course):

"sudo apt-get install --reinstall ttf-mscorefonts-installer"

This will present you with a text-based requester to use the arrow keys to highlight the "<ok>" at the bottom and hit return, thus accepting the license. From this point the install should go smoothly.


**PS:** Regarding the frustration mentioned above: I am not Japanese; I don't know any Japanese; and no Japanese is going to be using my systems, so , no, I do NOT need that 50 megabyte Japanese font. Please fix that in the future.

---

### Post by arpanaut on 2011-02-05
You might want to look at this Tutorial:  [http://ubuntuforums.org/showthread.php?t=140920&highlight=local+purge](http://ubuntuforums.org/showthread.php?t=140920&highlight=local+purge)

Tip #3 would address your concern over unnecessary fonts.
Good info about the license though.

---

### Post by Billsey on 2011-02-06
> **arpanaut said:**
> You might want to look at this Tutorial:  [http://ubuntuforums.org/showthread.php?t=140920&highlight=local+purge](http://ubuntuforums.org/showthread.php?t=140920&highlight=local+purge)

Tip #3 would address your concern over unnecessary fonts.

When an end user specifically unchecks an "update" so that that package is not wanted, that package should not get downloaded in the first place. I am one of those people that are still using dial-up, so that unnecessary download cost three+ hours of data transfer that could have gone to more productive endeavors. It is a bug that needs to be fixed.

---

