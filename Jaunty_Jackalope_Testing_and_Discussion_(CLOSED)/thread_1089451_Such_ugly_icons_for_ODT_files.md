---
title: "Such ugly icons for ODT files"
date: 2009-03-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Bou on 2009-03-07
Hi,

Since yesterday's updates, I've noticed that ODT files show a very, very ugly icon. Do you know if this is intentional?

---

### Post by lonniehenry on 2009-03-07
Appears to be intentional. All files using oo have variations of their openoffice program icons.  I find it informative not ugly.

---

### Post by cl333r on 2009-03-07
Is your post intentional?
I think the .odt icon is better than the one for .doc from your screenshot.

---

### Post by JohnJackson on 2009-03-07
Think I prefer the old ones. Why should .doc and .odt icons be different?

---

### Post by tgpraveen on 2009-03-07
> **johnjackson said:**
> think i prefer the old ones. Why should .doc and .odt icons be different?

+1

---

### Post by zekopeko on 2009-03-07
> **JohnJackson said:**
> Think I prefer the old ones. Why should .doc and .odt icons be different?

not all documents are created equal ;)

---

### Post by Bou on 2009-03-07
> **lonniehenry said:**
> Appears to be intentional. All files using oo have variations of their openoffice program icons.

Doc files don't, as seen in the screenshot. Also, I can't recall icons EVER representing specific applications instead of file types. Seems more of a Windows thing to me.

---

### Post by Sockerdrickan on 2009-03-07
Exactly how is the new icon ugly again?

---

### Post by Bou on 2009-03-08
I opened a bug: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/339590](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/339590)

---

### Post by durand on 2009-03-08
I noticed them as well. They're not ugly but I would prefer if the icon theme icons were used instead...This is just annoying. Or maybe I'm wrong?

---

### Post by Merk42 on 2009-03-08
I disagree that they look ugly and/or worse than the existing icons.
I agree that it is odd it's a specific application when, for example, audio files don't change their icon if it is set to open in Rhythmbox, Banshee, etc.

---

### Post by lonniehenry on 2009-03-08
I like the new icons.  I instantly know when I take files I created at home to use elsewhere they are saved in the right format.  I use a variety of machines and operating systems and I like the easy visual differenciation. The use of different icons for each of the different components of open office is especially nice and I like the tie-in to the openoffice main icons.

---

### Post by calc on 2009-03-08
> **Bou said:**
> I opened a bug: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/339590](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/339590)

As best as I can tell these icons are in gnome-icon-theme, not part of OOo.

---

### Post by KillerKiwi on 2009-03-08
Thumbnails are better
[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/25827](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/25827)

---

### Post by andrewabc on 2009-03-08
Intrepid .odt icons are the same as what original poster shows for .doc document.

It looks like this is not intentional, because my .ods icons in intrepid have specific icon as well (with spreadsheet stuff in them).

I doubt they are supposed to use generic openoffice icon for open document formats. If so they should change it back to what it is in Intrepid.

---

### Post by chrisccoulson on 2009-03-08
> **calc said:**
> As best as I can tell these icons are in gnome-icon-theme, not part of OOo.

Hi calc,

I commented on the bug report. The icons displayed in the OP's screenshot are shipped with the openoffice.org-common package and installed in /usr/share/icons/gnome. They weren't there before the re-sync with Debian, and I think that their presence might be a mistake (shouldn't they be in /usr/share/icons/hicolor instead)?

---

### Post by BCurtisWX on 2009-03-08
I don't know if any of you realize... but thats what the open office .odt file icon is REALLY supposed to look like.   Im glad they finally put it in.

---

### Post by andrewabc on 2009-03-08
> **BCurtisWX said:**
> I don't know if any of you realize... but thats what the open office .odt file icon is REALLY supposed to look like.   Im glad they finally put it in.

Then why in Intrepid does each openoffice filetype have a different icon?
The different icons for each filetype looks much better than one icon for all open document filetypes.

See my screenshot.

(unless you meant .odt was supposed to have its own icon)

Oops. I forgot to mention that I'm using calcs PPA and using OO 3.0.1

So I'm guessing my screenshots are the correct way.

---

### Post by lonniehenry on 2009-03-08
These are the type icons I have with Jaunty and oo3.0.1. I don't know where they came from.  Appeared after updates.

---

### Post by calc on 2009-03-08
I am going to try to get the ooo thumbnailer into Jaunty if possible which will make this entire issue moot. The problem in the past appears to have been that the icons were named incorrectly and Debian added symlinks to resolve the issue which caused the OOo icons to finally show up in Ubuntu.

---

### Post by bofphile on 2009-03-09
I hope you'll succeed calc. ;)
It seems strange to have thumbnails available for proprietary formats like .avi or .mov and not for an open format.

---

### Post by Bou on 2009-03-09
> **calc said:**
> I am going to try to get the ooo thumbnailer into Jaunty if possible which will make this entire issue moot.

Yes please.

---

### Post by andrewabc on 2009-03-09
> **lonniehenry said:**
> These are the type icons I have with Jaunty and oo3.0.1. I don't know where they came from.  Appeared after updates.

Those icons are much better than the enes I posted. They each have the OOo bird on top left corner so you know it is open document format, and the rest of icon is the type of odf and is color coded. Good design.

---

### Post by andrewabc on 2009-04-07
Openoffice update released in past day or so, which supposedly fixes the icons.

[changelog](http://changelogs.ubuntu.com/changelogs/pool/main/o/openoffice.org/openoffice.org_3.0.1-9ubuntu1/changelog)
- Remove hicolor and locolor icons. (LP: #339590)
- Update human icon theme. (LP: #348666)

Anyone know what they look like now?

[looks like](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/25827) they are still trying to get thumbnails in time for 9.04 release.

---

### Post by Bou on 2009-04-07
> **andrewabc said:**
> Openoffice update released in past day or so, which supposedly fixes the icons.

[changelog](http://changelogs.ubuntu.com/changelogs/pool/main/o/openoffice.org/openoffice.org_3.0.1-9ubuntu1/changelog)
- Remove hicolor and locolor icons. (LP: #339590)
- Update human icon theme. (LP: #348666)

Thank heavens!

> **andrewabc said:**
> Anyone know what they look like now?

Like your usual document types, tango-style. The same old ones we used to have.

---

### Post by andrewabc on 2009-04-08
> **Bou said:**
> Like your usual document types, tango-style. The same old ones we used to have.

I'm still confused which ones those are since so many icons were presented in this thread :P

Icon like in your first post/icon or the second icon? Or the icons that are posted on page 2? I see 3 different sets, so I have no idea which ones are used.

I just checked and they look like the icons in my 2nd page post. Which to me are worse than the icons in the post below mine showing 3 icons (by lonniehenry).

---

### Post by lonniehenry on 2009-04-08
Mine are back to the ones without the oo wing shapes. I really liked the oo wing shapes as they stood out showing exactly the format. Made it really easy to pick out on jumpdrives, etc.

---

### Post by andrewabc on 2009-04-08
> **lonniehenry said:**
> Mine are back to the ones without the oo wing shapes. I really liked the oo wing shapes as they stood out showing exactly the format. Made it really easy to pick out on jumpdrives, etc.

I think those icons are used in windows installations. I agree they look nice and are easily identifiable. The bird on top left identify OOo file, and the other part of icon identifies the type of OOo file. And they are color coded as well.

The current icons tell nothing about the filetype. :(

---

### Post by johnnybirdman on 2009-04-08
> **andrewabc said:**
> I think those icons are used in windows installations. I agree they look nice and are easily identifiable. The bird on top left identify OOo file, and the other part of icon identifies the type of OOo file. And they are color coded as well.

The current icons tell nothing about the filetype. :(

Don't know if these icons will get changed or not but I have to admit I liked the OOo icons better as well....

---

### Post by Bou on 2009-04-08
> **andrewabc said:**
> Icon like in your first post/icon or the second icon?

[http://ubuntuforums.org/attachment.php?attachmentid=105604&d=1236423098](http://ubuntuforums.org/attachment.php?attachmentid=105604&d=1236423098)

Now they look again like the one at the bottom.

---

### Post by Polygon on 2009-04-08
those icons (the blue/grey ones) are the windows icons....although i personally think they look fine, all documents should have either a thumbnail OF the document, or at least have all the same icon....being consistent is good =)

---

### Post by Bou on 2009-04-08
> **Polygon said:**
> those icons (the blue/grey ones) are the windows icons...

Sorry? No, they're Tango icons. They belong to the Gnome icon theme, and are not related to Windows in any way.

> **Polygon said:**
> all documents should have either a thumbnail OF the document, or at least have all the same icon....being consistent is good =)

Agreed. NOW all documents have the same icon, the blue / grey one.

---

### Post by lisati on 2009-04-08
What new icons? The one I saw has been around a while.....

---

### Post by andrewabc on 2009-04-08
> **Bou said:**
> Agreed. NOW all documents have the same icon, the blue / grey one.

Huh?
I see 4 different icons. A different one for each OO app (filetype).
I know OO draw has the ["picture" (mountain?) icon](http://ubuntuforums.org/attachment.php?attachmentid=105798&stc=1&thumb=1&d=1236559521)
They're the same as in my post with the screenshots on 2nd page.
So confusing :(

---

### Post by lonniehenry on 2009-04-08
Ok in the first screenshot these are the icons I have now. In the second screenshot are the icon that I had for a while.  I prefer the ones in second screenshot as they are easier to see the oo format and are really different than the MS Office style formats and that makes it easier to determine correct format for home/businessoffice use.  At the least we should be able to choose which set to use.

---

### Post by Polygon on 2009-04-08
> **Bou said:**
> Sorry? No, they're Tango icons. They belong to the Gnome icon theme, and are not related to Windows in any way.



Agreed. NOW all documents have the same icon, the blue / grey one.


the top one is what im talking about:

[http://ubuntuforums.org/attachment.php?attachmentid=105604&d=1236423098](http://ubuntuforums.org/attachment.php?attachmentid=105604&d=1236423098)

those are the icons i see in windows vista. or at least something very close to them....

---

