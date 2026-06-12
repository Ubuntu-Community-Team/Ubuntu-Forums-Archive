---
title: "Howto: Convenience additions"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bash on 2008-10-09
**About**

After installing a new vanilla Ubuntu, there are always quite a number of things I start changing. Things like the theme, add/remove programs and especially these little details that in my view should have been added since a long time to the default Ubuntu. Things like thumbnails previews for OOo documents, being able to use other video players than totem to preview video documents and so on. 

You can find tips & tricks on achieve all these things scattered all around the forum, but I thought it might be a good idea to make one topic about them, as people might have missed those threads.

If anybody happens to have other fancy little convenience additions, be sure to post them and I'll add them to the post.





**Add preview thumbnails for OpenOffice.org documents**

This will add a nice preview of the OOo document in nautilus. Just like it happens for PDF documents.

First create file named ooo2-thumbnailer in /usr/bin:

```
gksudo gedit /usr/bin/ooo2-thumbnailer
```

And copy in the following code:

```
#!/usr/bin/python

import zipfile
import sys
import os
import gnomevfs
from PIL import Image, ImageEnhance

# Color of the background
BackgroundColor = "white"

inURL=gnomevfs.get_local_path_from_uri(sys.argv[1])
outURL=sys.argv[2]
nothumbURL=os.getenv("HOME")+"/Templates"
nothumbList=nothumbURL.split(os.sep)
inList=inURL.split(os.sep)

if inList[1]==nothumbList[1] and inList[2]==nothumbList[2] and inList[3]!=nothumbList[3]:
	zip=zipfile.ZipFile(inURL,mode="r")
	picture=zip.read("Thumbnails/thumbnail.png")
	zip.close()
	thumbnail=open(outURL,"w")
	thumbnail.write(picture)
	thumbnail.write("/n")
	thumbnail.close()

	# Get File Extension    
	fileExtension = inURL[ len(inURL)-3 :].lower()

	thumbnail = Image.open(outURL).convert("RGBA")

	# Create new img with white bg
	final = Image.new("RGB", (thumbnail.size[0],thumbnail.size[1]), BackgroundColor)
	# Add thumbnail
	final.paste(thumbnail, None, thumbnail)
	# Save thumbnail
	final.save(outURL, "PNG")
```

Save and close the file. Then make it executable:

```
sudo chmod +x /usr/bin/ooo2-thumbnailer
```

Next create second file:

```
sudo gedit /usr/share/gconf/schemas/ooo2.schemas
```

And add the following:

```
<gconfschemafile>
    <schemalist>

        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.text/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.text/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.text/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.text/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
     

        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.spreadsheet/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.spreadsheet/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.spreadsheet/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.spreadsheet/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
	<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.graphics/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.graphics/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.graphics/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.graphics/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
	<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.formula/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.formula/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.formula/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.formula/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.presentation/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.presentation/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.presentation/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.oasis.opendocument.presentation/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.writer/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.writer/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.writer/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.writer/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
     

        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.calc/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.calc/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.calc/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.calc/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.draw/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.draw/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.draw/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.draw/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
	
	<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.math/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.math/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.math/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.math/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>
	<schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.impress/enable</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.impress/enable</applyto>
            <owner>ooo2-thumb</owner>
            <type>bool</type>
            <default>true</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>


        <schema>
            <key>/schemas/desktop/gnome/thumbnailers/application@vnd.sun.xml.impress/command</key>
            <applyto>/desktop/gnome/thumbnailers/application@vnd.sun.xml.impress/command</applyto>
            <owner>ooo2-thumb</owner>
            <type>string</type>
            <default>/usr/bin/ooo2-thumbnailer %u %o</default>
            <locale name="C">
                <short></short>
                <long></long>
            </locale>
        </schema>

    </schemalist>
</gconfschemafile>
```

Now save and close the file. The last step will be to tell GNOME to read the file and restart nautilus:

```
gconftool-2 --install-schema-file /usr/share/gconf/schemas/ooo2.schemas
```

```
killall -9 nautilus
```

Now you should be all set and have fancy little thumbnails.





**Using mplayer to create thumbnails/previews for video files**

If you happen to not have totem installed, you can use mplayer to generate previews of your video files.

First of lets make sure we have all the needed packages installed

```
sudo apt-get install mplayer imagemagick
```

Next up we need to download the mplayer thumbnails script and install it:

```
wget http://me2030581.googlepages.com/mplayer-video-thumb-1.3-3.tar.bz2
tar -xf mplayer-video-thumb-1.3-3.tar.bz2
cd mplayer-video-thumb-1.3-3
chmod +x setup.sh
sudo ./setup.sh
./gconf.sh
```

Now mplayer should create video previews for you. If you happen to have failed preview icons, just delete those so that mplayer can recreate them:

```
rm -rf $HOME/.thumbnail/fail/
```





**Getting QT applications to use GTK themes**

One of the developers at Trolltech create this fancy little QT Style that allows you to use GTK themes for QT applications. Sadly it is not (yet?) available in the Repos, so we have to compile it ourselves.

First off lets install all the needed packages:

```
sudo apt-get install subversion build-essential checkinstall libqt4-dev libgtk2.0-dev qt4-qtconfig
```

After we need to get the code, compile it:

```
svn co svn://labs.trolltech.com/svn/styles/gtkstyle
cd gtkstyle
qmake && make
```

When that is done, you have two choices: Either to install the code directly, using:

```
sudo make install
```

or to create a .deb package that will then be automatically be installed, using:

```
sudo checkinstall
```

I prefer the second method, as it allows me to easily remove the functionality using synaptic.

(If you use checkinstall and aren't 100% what all the options mean, just keep pressing Enter. On the other hand if that is the case you probably should be compiling and using Beta releases in the first place ;) )

To finish off we just need to open the QT Config and set the style to GTK there (Don't forget to click "File" &#8594; "Save" or you settings won't be remembered).

*Note:* The GTK style you set in qtconfig only works for **QT** applications (VLC, Virtualbox, ...) but does not change the style of **KDE** applications (KTorrent, ...).





**Thanks**

[list][*]Thanks to [minio](http://ubuntuforums.org/member.php?u=2264) for his great tutorial on adding OOo thumbnails ([Link](http://ubuntuforums.org/showthread.php?t=76566))
[*]Thanks to [mysticmatrix](http://ubuntuforums.org/member.php?u=344753) for his/her great tutorial on using mplayer to generate video previews ([Link](http://ubuntuforums.org/showpost.php?p=3270013&postcount=3))
[*]Thanks to [Ravinder Rathi](http://me2030581.googlepages.com/home) for writing the great mplayer video thumbnailer ([Link](http://me2030581.googlepages.com/))
[*]Thanks to [Jens](http://labs.trolltech.com/blogs/author/jbache/) at Trolltech for creating the great QT Style ([Link](http://labs.trolltech.com/blogs/2008/05/13/introducing-qgtkstyle/))
[*]Thanks to [paulms](http://ubuntuforums.org/member.php?u=390452) for the great install compile instructions for qgtkstyle ([Link](http://ubuntuforums.org/showpost.php?p=5006093&postcount=44))[/list]

---

