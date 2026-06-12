---
title: "nihongo benkyo"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by mazzzterZ on 2008-08-17
hi !
Recently I started learning japanese and I remembered that under windows there was a dictionary named nihongo benkkyo. So I searched through google and found out that it can be used under linux so I wanted to install it... and here is the problem I can't :( . I'm using Ubuntu 8.04LT. I installed all things in the README file(or so I think) except for one libsqlite3(I think). I had problems installing it. I managed to ./configure it but couldn't compile it with the make command:
> Requirements
------------

    Ruby >= 1.8.0:              [http://www.ruby-lang.org](http://www.ruby-lang.org)
    GTK+ >= 2.6:                [http://www.gnome.org](http://www.gnome.org)
    libxml2 >= 2.6.22 [**]:     [http://www.xmlsoft.org](http://www.xmlsoft.org)
    Ruby-GetText >= 0.6.1:      [http://ponx.s5.xrea.com/hiki/ruby-gettext.html](http://ponx.s5.xrea.com/hiki/ruby-gettext.html)
    Ruby-GNOME2 >= 0.14.1 [*]:  [http://ruby-gnome2.sourceforge.jp](http://ruby-gnome2.sourceforge.jp)
    libsqlite3 >= 3.2.1:        [http://www.sqlite.org](http://www.sqlite.org)         
    Sqlite3/Ruby >= 1.1.0:      [http://rubyforge.org/projects/sqlite-ruby/](http://rubyforge.org/projects/sqlite-ruby/)
    Intltool:                   [http://freedesktop.org/wiki/Software_2fintltool](http://freedesktop.org/wiki/Software_2fintltool)

    [*]: Required libraries are: Ruby/Libglade2, Ruby/Gtk2 and Ruby/GdkPixbuf2.
    [**]: Only required if you want the import facility.

After I finish installing them I tried installing the dictionary. I followed the steps: 
> Install 
-------

    * With the import facility:

        $ ruby setup.rb config
        $ ruby setup.rb setup
        ($ su)
        # ruby setup.rb install

    * Without the import facility:
    
        ($ su)
        # ruby setup.rb all --without-ext

Installation goes ok. I didn't see any errors or missing files... but when I use the command in the README file:
> Usage
-----

    $ nihongobenkyo
i get the message:
> mazzzterz@mazzzterz-desktop:~/Desktop/nihongobenkyo-0.3.1$ nihongobenkyo
/usr/local/lib/ruby/site_ruby/1.8/nihongobenkyo/ui.rb:18:in `require': no such file to load -- libglade2 (LoadError)
	from /usr/local/lib/ruby/site_ruby/1.8/nihongobenkyo/ui.rb:18
	from /usr/local/lib/ruby/site_ruby/1.8/nihongobenkyo.rb:59:in `require'
	from /usr/local/lib/ruby/site_ruby/1.8/nihongobenkyo.rb:59
	from /usr/local/bin/nihongobenkyo:7:in `require'
	from /usr/local/bin/nihongobenkyo:7

I don't know what to do from this point forward. Please if you can help!

---

### Post by Partyboi2 on 2008-08-17
Another way you could try is to download and install fantasdic
```
sudo apt-get install fantasdic
``` then start the program and go to "Edit" then "Preferences" On the first tab "Dictionaries"  click on "add" On the first tab "Server" Add "Japanese" for name and change the "server" field to "nihongobenkyo.org" then press ok. This should now add the Japanese dictionary. See [[COLOR=Blue]here[/COLOR]]("http://www.nihongobenkyo.org/") for more details

---

### Post by mazzzterZ on 2008-08-17
> **Partyboi2 said:**
> Another way you could try is to download and install fantasdic
```
sudo apt-get install fantasdic
``` then start the program and go to "Edit" then "Preferences" On the first tab "Dictionaries"  click on "add" On the first tab "Server" Add "Japanese" for name and change the "server" field to "nihongobenkyo.org" then press ok. This should now add the Japanese dictionary. See [[COLOR=Blue]here[/COLOR]]("http://www.nihongobenkyo.org/") for more details

I did what you said and the dictionary works... but there are two things that trouble me:
1st - I can't write in romanji (it's not really a problem because I can write in hiragana and katakana but there is the annoying step of pressing 'Ctrl + Space' and the surprise I get when I change to write somewhere else)

2nd - the kndjis are small and it's really hard to distinguish the strokes of kanjis that aren't familiar. I can change the fornt size but all leters will become big and it will become a mess.

I don't believe there to be a solution for these with this dictionary but I just wanted to state them and thanks for the replay. The dictionary ahve a good side too. it shows edict-fr, jmdict and kanjidic2 in one window and I don't ahve to switch between them.


EDIT: I just wanted to ask if I can download the database of words instead of searching for them through internet because there are times when I won't have internet on my computer and yet I'll need the dictionary.

---

### Post by Partyboi2 on 2008-08-17
I don't actually use the program so not sure about the database. I had another look at the error you were getting when you were compiling and it looks like you needed to install libglade2-ruby1.8 package I guess atleast now you get to try out the one you were trying to compile or the fantasdic application to see what one best suits.

---

