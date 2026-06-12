---
title: "Permisos de DVD que no se pueden modificar."
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by elmat0 on 2012-02-17
Hello people.

Well, I tell you my problem. Im trying to install GTA: SA to kill boredom and to install you have to put on 'setup.exe' properties and modify the permissions, setting it to 'Read and write' but I can not change ... this is what I get.

[IMG]http://img821.imageshack.us/img821/4248/screenshotyca.png[/IMG]



Any solution? Thank you.

---

### Post by coffeecat on 2012-02-17
Hi and welcome to the forum. Please note that English is the common language of the main part of the forum, but you may post in Spanish in one of the Spanish-speaking forums in the LoCo section if you prefer:

[http://ubuntuforums.org/forumdisplay.php?f=183](http://ubuntuforums.org/forumdisplay.php?f=183)

Good luck with getting help for your problem.

Please blame Google translate if the Spanish part of this post sounds strange. :wink:

---

Hola y bienvenido al foro. Observe que el Inglés es el idioma común de la parte principal del foro, pero es posible publicar en español en uno de los foros de habla española en la sección de LoCo, si lo prefiere:

[http://ubuntuforums.org/forumdisplay.php?f=183](http://ubuntuforums.org/forumdisplay.php?f=183)

Buena suerte con conseguir ayuda para su problema.

Por favor, culpar a Google Translate, si la parte española de este post suena extraño. :wink:

---

### Post by josephmills on 2012-02-17
please open your terminal and change  dir   ```
cd /media/GTA_SAN_ANDREAS
``` then ```
sudo -i 
``` then 
```
chmod +x *.exe
``` then ```
exit
```
 hope this 

spanish 


por favor, abra el terminal y cambie dir
```
cd /media/GTA_SAN_ANDREAS
```
entonces
```
sudo -i 
```
entonces
 ```
chmod +x *.exe
```
 entonces
```
exit
```
Esperamos que esto ayude

también hay foros de Ubuntu para el español que se encuentran aquí. Veamos ahora cómo funciona
Podría tener que copiar el CD a su hardrive a continuación, ejecutar permisos.

---

### Post by elmat0 on 2012-02-17
Uhm hi josephmills, thanks for answer my question but... look at that.


[IMG]http://desmond.imageshack.us/Himg641/scaled.php?server=641&filename=screenshot1lx.png&res=medium[/IMG]

What's happening? Did I do what you said right?

---

### Post by elmat0 on 2012-02-17
And that...

[IMG]http://desmond.imageshack.us/Himg526/scaled.php?server=526&filename=screenshot1ru.png&res=medium[/IMG]

Please, help me.

---

### Post by josephmills on 2012-02-17
it looks like it is read only do you nned to copy like this 

```
cd ~ && mkdir san_an && cd /media/GTA_SAN_ANDREAS && cp * ~/san_an/ && cd ~/san_an && chmod +x *.exe && wine setup.exe
```


then  
```
sudo gedit /usr/share/applications/GTA.desktop

```
then add this and save 
```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Name=GTA
GenericName=grand theft auto san 
Exec=/home/$USER/san_an/setup.exe
Icon=/usr/share/icons/gta.png 
Categories=Game;

```

you might want to change this after install 

Exec=/home/$USER/san_an/setup.exe


but it should be in the menu now. under applications --> games --> GTA

Hope this helps

---

### Post by elmat0 on 2012-02-17
> **josephmills said:**
> it looks like it is read only do you nned to copy like this 

```
cd ~ && mkdir san_an && cd /media/GTA_SAN_ANDREAS && cp * ~/san_an/ && cd ~/san_an && chmod +x *.exe && wine setup.exe
```then  
```
sudo gedit /usr/share/applications/GTA.desktop

```then add this and save 
```

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Name=GTA
GenericName=grand theft auto san 
Exec=/home/$USER/san_an/setup.exe
Icon=/usr/share/icons/gta.png 
Categories=Game;

```you might want to change this after install 

Exec=/home/$USER/san_an/setup.exe


but it should be in the menu now. under applications --> games --> GTA

Hope this helps

Thanks for answer, but...


[IMG]http://img267.imageshack.us/img267/9283/screenshot5ru.png[/IMG]

And, look at this...

[IMG]http://desmond.imageshack.us/Himg193/scaled.php?server=193&filename=screenshotbph.png&res=medium[/IMG]

0 KB... why?

---

### Post by elmat0 on 2012-02-17
Can someone help me?

---

