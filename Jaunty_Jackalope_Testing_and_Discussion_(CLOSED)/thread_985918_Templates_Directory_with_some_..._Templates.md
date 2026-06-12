---
title: "Templates Directory with some ... Templates?"
date: 2008-11-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Geekkit on 2008-11-18
The templates directory is usually empty although it's there for the ability to right-click in Nautilus and create a new document. I think some default blank documents with their already existing file associations with applications would offer new users a more familiar feel. In the very least (and because these applications already exist on installation), the following document templates would be useful to have for the right-click:

- Open Office Documentation
- Open Office Presentation
- Open Office Spreadsheet
- GIMP Image
- Rename "empty file" and call it "Simple Text File"
- Inkscape Document

Very little effort and yet new users will most likely find this quite helpful methinks.

---

### Post by olskar on 2008-11-18
I agree. Check my earlier thread about that:
[http://ubuntuforums.org/showthread.php?p=6036030](http://ubuntuforums.org/showthread.php?p=6036030)

As it is now, all it does is confusing people!

I have also reopened bug [https://bugs.launchpad.net/nautilus/+bug/3235](https://bugs.launchpad.net/nautilus/+bug/3235)

It's an old bug...since 2005-10-16..perhaps they don't care about such old bugs?

---

### Post by Geekkit on 2008-11-18
> **olskar said:**
> It's an old bug...since 2005-10-16..perhaps they don't care about such old bugs?

Apparently. :/

---

### Post by danf_1979 on 2008-11-18
Is there any documentarion on this topic?

---

### Post by andrewabc on 2008-11-18
This should definitely be done.
I've been using ubuntu off and on since 2006, and I only figured this out 2 weeks ago.

Something as simple as this should be done. I had no idea I had to put templates in a directory in order to get items to appear in a menu. I had to google search and read a how-to to figure it out.

And people wonder why linux is not mainstream.

---

### Post by Geekkit on 2008-11-18
> **andrewabc said:**
> This should definitely be done.
I've been using ubuntu off and on since 2006, and I only figured this out 2 weeks ago.

Something as simple as this should be done. I had no idea I had to put templates in a directory in order to get items to appear in a menu. I had to google search and read a how-to to figure it out.

And people wonder why linux is not mainstream.

I would equate this blind spot to building an Audi car model and forgetting to connect the speaker wires in the car to the car's stereo.

It's not hard to make yourself a bunch of templates but like you've stated, you had no idea and this isn't really documented anywhere other than in these forums.

Omissions like this really are a shame: they're so easy to solve and offer such a great utility to the user.

---

### Post by chrisccoulson on 2008-11-18
The problem is that Nautilus currently only supports per-user ~/Templates folders. It doesn't support reading templates from a system-wide location, which makes it very difficult for distributors to ship default templates (you'd need to give every user their own set of templates or symlink each users ~/Templates folder to a system-wide location, which would then mean that users can't customize their templates. The other alternative would be to create a set of templates in /etc/skel, which new users would get when they are added to the system. With this method, users would be able to edit their templates, but they wouldn't automatically get access to new templates as they are added to the system).

This has been discussed upstream, and they are reluctant to modify Nautilus to read templates from a system-wide folder as well as the existing per-user ~/Templates folder. I will try and find the upstream discussion and provide you with a link.

---

### Post by danf_1979 on 2008-11-18
> **andrewabc said:**
> This should definitely be done.
I've been using ubuntu off and on since 2006, and I only figured this out 2 weeks ago.

Something as simple as this should be done. I had no idea I had to put templates in a directory in order to get items to appear in a menu. I had to google search and read a how-to to figure it out.

And people wonder why linux is not mainstream.

Andrew, any link to that howto? :)

---

### Post by Geekkit on 2008-11-18
> **danf_1979 said:**
> Andrew, any link to that howto? :)

Do this:

1) In nautilus, CTRL-H (show hidden files ... i.e., that start with a '.')

2) Create a '.templates' directory, preferably in the root of your home folder (but doesn't have to). You can call it '.foo' if you want to ... actually you can call it 'foo' (without the dot) or 'MaryJane' if that's what floats your boat. But use a dot at the beginning otherwise the file won't be hidden anymore and it will show up within the root of your home directory.

3) Navigate (still showing hidden files) into your ~/.config directory. This directory has a file called user-dirs.dirs. Open it up in Gedit. The line that says:
XDG_TEMPLATES_DIR="$HOME/.Templates"
Change to:
XDG_TEMPLATES_DIR="$HOME/.templates" or .foo or whatever you wanted to call your hidden templates directory and where ever you put it.

4) Save changes, close Gedit
5) Populate your .templates directory (again, if you called it .foo, your .foo directory) with whatever files you want: K3D project files, xcf files, SVG, php, html, xml, java, whatever. You can even put directories in it too.

Directories show up as new sub menus. Put spaces in the name if you want it to look pretty in your pop up menu items in Nautilus when you right click.

I have zip files that contain Java EE projects with my own custom Ant script to build the project and that's okay too. All this is really doing is copying a file and presenting it to you as a 'template'. The other side of this of course is the file association that Nautilus has with that file extension so that when you click on that 'template' it opens up the respective associated application. But then again that's all Windows does too :P

---

### Post by andrewabc on 2008-11-18
> **danf_1979 said:**
> Andrew, any link to that howto? :)

Looking through firefox history, I believe this is the one I used.

[Add Your Document Templates to GNOME](http://tombuntu.com/index.php/2008/02/13/add-your-document-templates-to-gnome/)

---

### Post by Geekkit on 2008-11-19
> **chrisccoulson said:**
> The problem is that Nautilus currently only supports per-user ~/Templates folders. It doesn't support reading templates from a system-wide location, which makes it very difficult for distributors to ship default templates (you'd need to give every user their own set of templates or symlink each users ~/Templates folder to a system-wide location, which would then mean that users can't customize their templates. The other alternative would be to create a set of templates in /etc/skel, which new users would get when they are added to the system. With this method, users would be able to edit their templates, but they wouldn't automatically get access to new templates as they are added to the system).

This has been discussed upstream, and they are reluctant to modify Nautilus to read templates from a system-wide folder as well as the existing per-user ~/Templates folder. I will try and find the upstream discussion and provide you with a link.

If you find it, I would be interested in seeing that discussion. I think I understand what you are saying, that is a bit of a conundrum.

---

### Post by Wolki on 2008-11-20
Upstream discussion from when the templates feature was first implemented: [http://mail.gnome.org/archives/nautilus-list/2003-December/msg00128.html](http://mail.gnome.org/archives/nautilus-list/2003-December/msg00128.html)

Recent upstream discussion: [http://mail.gnome.org/archives/nautilus-list/2008-June/msg00123.html](http://mail.gnome.org/archives/nautilus-list/2008-June/msg00123.html)

Ubuntu bug marked invalid: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/23332](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/23332)

Ubuntu discussion: [https://lists.ubuntu.com/archives/ubuntu-desktop/2008-October/001816.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2008-October/001816.html)

*shameless plug* My idea: [http://bugzilla.gnome.org/show_bug.cgi?id=558435#c2](http://bugzilla.gnome.org/show_bug.cgi?id=558435#c2)

---

### Post by Gina on 2008-11-20
> **andrewabc said:**
> This should definitely be done.
I've been using ubuntu off and on since 2006, and I only figured this out 2 weeks ago.

Something as simple as this should be done. I had no idea I had to put templates in a directory in order to get items to appear in a menu. I had to google search and read a how-to to figure it out.

And people wonder why linux is not mainstream.+1  Things like GIMP and Open Office have a steep learning curve and templates for common applications would definitely be very helpful.  When I first started using Open Office and GIMP (in Windows XP actually) I was quite surprised that there were no templates for making standard items.  So I think this may be more an issue with the open source applications than Ubuntu (or even Linux) particularly. It would be really helpful if we could extend the great usability of Ubuntu to the applications.

As an aside and off-topic really but illustrates how much Ubuntu has progressed in the usability stakes.  I reinstalled Windows XP followed by Ubuntu 8.10 on my P4 machine after I had messed up with a cleaning exercise.  This was a plain XP CDROM rather than an image of the factory hard disk setup and took over an hour to install with user intervention every ten minutes or so.  The (Live CD) Ubuntu install only took just over 20 minutes and everything could be set up in the first few minutes then left to do it's stuff.

---

### Post by Geekkit on 2008-11-20
> **Wolki said:**
> Upstream discussion from when the templates feature was first implemented: [http://mail.gnome.org/archives/nautilus-list/2003-December/msg00128.html](http://mail.gnome.org/archives/nautilus-list/2003-December/msg00128.html)

Recent upstream discussion: [http://mail.gnome.org/archives/nautilus-list/2008-June/msg00123.html](http://mail.gnome.org/archives/nautilus-list/2008-June/msg00123.html)

Ubuntu bug marked invalid: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/23332](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/23332)

Ubuntu discussion: [https://lists.ubuntu.com/archives/ubuntu-desktop/2008-October/001816.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2008-October/001816.html)

*shameless plug* My idea: [http://bugzilla.gnome.org/show_bug.cgi?id=558435#c2](http://bugzilla.gnome.org/show_bug.cgi?id=558435#c2)

Shameless indeed. :) Seriously though, your idea is a good one, thanks for the post.

A couple of other ideas come to my mind (not necessarily mutually exclusive to yours):
- Add at least the OO templates to the templates directory via a script, each time a user account is created
- Have a Gnome panel applet that allows you to add more templates  - which goes to a particular web site and grabs said templates

I think what the point here is that adding a templates directory and putting nothing in it and not documenting that you can put things in it is a rather silly solution.

---

### Post by BwackNinja on 2008-11-20
I'd say to have the addition of templates to be set as something in the nautilus right-click menu instead of somewhere on the panel.

---

