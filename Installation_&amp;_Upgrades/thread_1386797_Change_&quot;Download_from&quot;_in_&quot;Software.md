---
title: "Change &quot;Download from&quot; in &quot;Software sources&quot; to &quot;Main server&quot; in terminal"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by gubbi.fisk on 2010-01-21
Hey

I'm trying to create a "install script" that will do all sorts of things. One of these things is to change "Download from" in "Software sources" to "Main server". This is because the local (Danish) server seems to have some issues, the easy work around is to use the "Main server". I can enable components from terminal with:
```
sudo software-properties-gtk --enable-component=COMP
```
But I can't seem to change the "Download from". I'm also interested in changing the "Release upgrade" and the "Submit statistical information".

I hope you can help!

- Gubbi.fisk

---

### Post by gubbi.fisk on 2010-01-22
Hello guys...

---

### Post by gubbi.fisk on 2010-01-25
Is there no one, out there, who knows something?!?

---

### Post by gubbi.fisk on 2010-03-12
Hey I wrote one my self! This bash script changes the "Download from" from the danish server to main server.

```
	cd /etc/apt/
	sudo rm sources.list.save
	sudo cp sources.list sources0.list
	cat "sources0.list" | sed 's/dk\.archive\.ubuntu\.com/archive\.ubuntu\.com/g' | sudo tee "sources1.list"
	cat "sources1.list" | sed 's/\#\ deb\ http\:\/\/archive\.canonical\.com\/ubuntu/deb\ http\:\/\/archive\.canonical\.com\/ubuntu/g' | sudo tee "sources2.list"
	cat "sources2.list" | sed 's/\#\ deb\-src\ http\:\/\/archive\.canonical\.com\/ubuntu/deb\-src\ http\:\/\/archive\.canonical\.com\/ubuntu/g' | sudo tee "sources3.list"
	cat "sources3.list" | sed 's/\#\ deb\ http\:\/\/dk\.archive\.canonical\.com\/ubuntu/deb\ http\:\/\/archive\.canonical\.com\/ubuntu/g' | sudo tee "sources4.list"
	cat "sources4.list" | sed 's/\#\ deb\-src\ http\:\/\/dk\.archive\.canonical\.com\/ubuntu/deb\-src\ http\:\/\/archive\.canonical\.com\/ubuntu/g' | sudo tee "sources5.list"
	cat "sources5.list" | sed 's/deb\ http\:\/\/dk\.archive\.canonical\.com\/ubuntu/deb\ http\:\/\/archive\.canonical\.com\/ubuntu/g' | sudo tee "sources6.list"
	cat "sources6.list" | sed 's/deb\-src\ http\:\/\/dk\.archive\.canonical\.com\/ubuntu/deb\-src\ http\:\/\/archive\.canonical\.com\/ubuntu/g' | sudo tee "sources7.list"
	sudo rm sources.list
	sudo rm sources0.list
	sudo rm sources1.list
	sudo rm sources2.list
	sudo rm sources3.list
	sudo rm sources4.list
	sudo rm sources5.list
	sudo rm sources6.list
	sudo mv sources7.list sources.list
	cd ~/
	sudo apt-get update
```

---

### Post by gubbi.fisk on 2010-03-12
Ups, I forgot to say it also activates the two Canonical repos in "Other software"!

---

