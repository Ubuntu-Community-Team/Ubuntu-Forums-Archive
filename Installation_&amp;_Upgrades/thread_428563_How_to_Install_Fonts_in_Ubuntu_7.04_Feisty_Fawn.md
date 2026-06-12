---
title: "How to Install Fonts in Ubuntu 7.04 Feisty Fawn"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by Whatawonderfulday on 2007-04-30
Dear Ubuntufolk:

I have been looking at how to install fonts in Ubuntu and I am confused.

I have downloaded with Synaptic the mscorefonts package, but I need to integrate a much wider number of fonts for special use including multinlanguage.

There are two cases:

1.   I have a file full of fonts that I want to integrate into the Ubuntu shared fonts.  The directions on the Open Office FAQ are somewhat confusing to a newbie to Ubuntu, especially since I don't know by heart the commands for copying the source file to the proper directory.  Under FC4 it was a fairly straightforward matter.

2.  I want to download fonts for special languages from the Internet, save them somewhere and then integrate them into Ubuntu.

In both cases I want the fonts to be available for use in Open Office, especially the word processor (writer).

Thanks.

Whatawonderfulday

---

### Post by Whatawonderfulday on 2007-05-02
I feel like the teacher who has to give the answer because none of the students did.  Here is how you do it:

In a terminal as root:

 /usr/lib/openoffice/program/./spadmin

Click 'Fonts' when the pop-up for the spadmin program appears.

Click 'Add' when the pop-up for fonts appears.

Browse (... button) to the folder which contains the fonts you want to add.  In the select path window you should see the various fonts listed.  Click 'OK'.

On the previous fonts pop-up you should see both your folder name (next to the ... button) and a listing of all the fonts in the folder.

Make a selection.  I simply clicked 'Select All'.

Click 'OK' on the same pop-up.

You will get a pop-up if you are attempting to install a font which already exists (a likely possiblity if you are really merging font folders from various sources).  On the assumption that the fonts already installed shouldn't be disturbed, I clicked 'None' on this pop-up.  The 'None' is equivalent to 'No to All'.  This means that although I 'selected all', I am only installing fonts that are not already installed.

Click 'OK'.

As many fonts as you are allowing will now be installed.

Click 'Close' as many times as necessary to back out of all the pop-ups and close the spadmin program.

You're set--as far as I know.

Now--how do I configure the FAX services?  But that's for the next thread...

Whatawonderfulday.

---

