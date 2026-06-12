---
title: "Installing Go language"
date: 2020-08-23
forum: Installation &amp; Upgrades
---

### Post by federicuz on 2020-08-23
Hi community, I need to get some packages with "go get" and run them. I don't need to write any Go code myself. What are the recommended steps?

Note: I don't want to use a package that requires me to set any variable, modify any file, or copy anything manually. I am grateful to anyone who answers, but I'm not going to install packages that only do part of the job. If proper packages don't exist, I'm ok with doing the whole procedure manually.

---

### Post by CelticWarrior on 2020-08-23
Welcome.

Search for 'golang' in the software store and you may find what you're looking for.
Otherwise, download it from [here]("https://golang.org/dl/") and follow [this instructions]("https://tecadmin.net/install-go-on-ubuntu/") that should be the same also for the current 20.04.

---

### Post by federicuz on 2020-08-30
The package in Ubuntu official repos does not set environment variables. I'm not sure which use cases it is meant to cover, but in my case I'm strictly against partially manual and partially automatic installations.

---

### Post by Impavidus on 2020-08-31
A deb package might drop a file in /etc/environment.d/ to set an environment variable for all users, but I don't think it's a serious error if it doesn't. I would expect applications to show useful behaviour if no environment variable had been set, other than the standard ones that should be present always.

Setting the environment variable yourself isn't partially manual installation. It's configuration for individual users. Yes, this is nitpicking.

---

