---
title: "How to set a image for a mimetype, for example .java files"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by shakaran on 2009-10-03
Hi I have the theme Humanity installed, but this theme put a icon for application/x-java (.class files), but it dont for source code java files (text/x-java).

I see that other theme oxyge have a icon and I try to copy for Humanity, but it dont work:

cp /usr/share/icons/oxygen/32x32/mimetypes/application-x-java.png /usr/share/icons/Humanity/mimes/32/text-x-java.png

Then how to set that icon?

PS: I see this bug [https://bugs.launchpad.net/ubuntu/+source/gnome-icon-theme/+bug/45100](https://bugs.launchpad.net/ubuntu/+source/gnome-icon-theme/+bug/45100) but this bug have 3 years!! Only for put a simple icon? This should be a papercut.

I attach the image for copy.

---

### Post by anagor on 2009-10-03
I think you should look here: [http://ubuntuforums.org/showthread.php?t=912692](http://ubuntuforums.org/showthread.php?t=912692)
reply #8.
or here: [http://ubuntuforums.org/showthread.php?t=302549](http://ubuntuforums.org/showthread.php?t=302549)
reply #9.
two different approaches, whichever suits you best :)

---

### Post by shakaran on 2009-10-04
Well, I did:
```
cp /usr/share/icons/oxygen/32x32/mimetypes/application-x-java.png ~/.icons/text-x-java.png

```

It don't work.

---

### Post by anagor on 2009-10-05
It's not enough to copy the icon file,
you need to create new or edit existing xml file as discussed in those threades from my previous post.

---

### Post by shakaran on 2009-10-05
I did this

```
touch ~/.local/share/mime/packages/tex-x-java.xml
```

Put inside

```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
	<mime-type type="text/x-java">
		<comment>Java source code</comment>
		<glob pattern="*.java"/>
	</mime-type>
</mime-info>
```

And run
```
update-mime-database ~/.local/share/mime/
```

Nothing, it dont work yet. Some mistake more is remaining.

---

