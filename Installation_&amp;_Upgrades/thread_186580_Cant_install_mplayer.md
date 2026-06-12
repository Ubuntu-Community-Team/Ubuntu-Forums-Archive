---
title: "Cant install mplayer"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by KooT on 2006-06-02
apt-get install mplayer-custom
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci... Gotowe
Nie uda&#322;o si&#281; zainstalowa&#263; niektórych pakietów. Mo&#380;e to oznacza&#263;,
&#380;e za&#380;&#261;dano niemo&#380;liwej sytuacji lub u&#380;ywasz dystrybucji niestabilnej,
w której niektóre pakiety nie zosta&#322;y jeszcze utworzone lub przeniesione
z katalogu Incoming ("Przychodz&#261;ce").

Poniewa&#380; za&#380;&#261;dno tylko jednej operacji, jest bardzo prawdopodobne, &#380;e
danego pakietu po prostu nie da si&#281; zainstalowa&#263; i nale&#380;y zg&#322;osi&#263; w nim
b&#322;&#261;d.
Nast&#281;puj&#261;ce informacje mog&#261; pomóc rozpozna&#263; sytuacj&#281;:

Nast&#281;puj&#261;ce pakiety maj&#261; niespe&#322;nione zale&#380;no&#347;ci:
  mplayer-custom: Wymaga: aalib1 (>= 1.2)
E: Pakiety s&#261; b&#322;&#281;dne

---

### Post by woot on 2006-06-02
I dont understand the language but i think its says you need aalib >= 1.2
which the apt doesnt find in its repos, dont know why as you can find it eassy at this link: [http://packages.ubuntu.com/dapper/libs/libaa1](http://packages.ubuntu.com/dapper/libs/libaa1) 

You can download it there and install it manually by 
```
sudo dpkg -i downloadedpackage.deb
```

the other dependencies are here:
[http://packages.ubuntu.com/dapper/graphics/mplayer](http://packages.ubuntu.com/dapper/graphics/mplayer)

Perhaps

```
sudo apt-get update
```

might refresh your package list and then you might be able just to install mplayer like you were trying to

---

### Post by KooT on 2006-06-02
[QUOTE=woot]
[...]
might refresh your package list and then you might be able just to install mplayer like you were trying to[/QUOTE]

I had bad multiverse repo...
Thanks for replay ;)

---

