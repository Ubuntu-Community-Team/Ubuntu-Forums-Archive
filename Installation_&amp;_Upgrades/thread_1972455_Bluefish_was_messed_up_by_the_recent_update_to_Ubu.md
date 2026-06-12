---
title: "Bluefish was messed up by the recent update to Ubuntu 12.04"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by DavidVS on 2012-05-03
Hi again!

Updating to Ubuntu 12.04 was almost without incident.  OpenOffice and a few other applications forgot my "recent files" lists.

The only significant problem is making Bluefish look nice.

(Bluefish used to require setting colors for each aspect of HTML code, as I blogged [here]("http://davidvs.blogspot.com/2010/06/more-bluefish-color-customization.html").  Now it first asks for "text styles" and then each programming language refers to those.  Thus I can define the text style of *comment* and simply have all my programming languages use that text style instead of repeatedly defining what a comment should look like for each individual language.  Nice!  But new work to do.)

My problem is simple: no matter what colors I pick for foreground and background (in menu Edit -> Preferences and then sidebar Editor Settings -> Font & Colors) I cannot see what text blocks I select with the cursor.  The "highlighting" with the cursor only makes the foreground change to the default foreground color.  This is barely noticeable when I happen to select a colored HTML tag, and invisible when I select plain text!

Thanks for any help!

UPDATE: I should add the default colors DO work after I rename the .bluefish directory in my home directory.  But as soon as I change the background color, that cursor-highlighting issue returns!

UPDATE 2: Well, I can use Compiz to enable Accessability -> Negative and do my typing with an easy on the eyes color scheme that way.  So problem is not solved, but a workaround is easy.

---

### Post by MrPizzaLust on 2012-09-18
Color schemes drive me nuts.  Applications rarely offer suitable configuration options for what I'm trying to accomplish, and the OS is seemingly working against me at every turn.

Bluefish Text Color Issues
Configurations: Edit>Preferences>Editor Settings>Font & Color
1. Default configuration has the 'background color' and the 'selected text' colors matching. Someone, please add a color picker for 'selected text'.
2. When checking the "Use System Wide Color Settings", the bluefish specified colors stay in effect.
3. Setting the System 'Selection Background' color has no effect on BF.

To get the editor to behave somewhat properly I have to set the 'Background Color' to white and the 'Current Line' color to something else. I chose a light blue.

BF currently has no IRC channel, which seems a bit weird for a project this size.

Hope this helps someone until they sort this out.

---

### Post by millo on 2012-11-14
I've got the same issue and I've not found a solution yet, however accidentally I came across this but if I hit <ctrl> <alt> <s> (I was trying to do a 'Save All' but got it wrong. It concertinas the app into just the title bar and when I press the same keys again so that it appears again the select background is now mysteriously working. Hope they will sort this soon!

---

### Post by andrew.46 on 2012-11-15
> **millo said:**
>  Hope they will sort this soon!

Are you running the most recent version?

```

andrew@skamandros~$ **[COLOR="Red"]bluefish --version[/COLOR]**
Bluefish Editor 2.2.3
Visit us at http://bluefish.openoffice.nl

```

---

