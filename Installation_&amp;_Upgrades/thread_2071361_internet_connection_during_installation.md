---
title: "internet connection during installation"
date: 2012-10-15
forum: Installation &amp; Upgrades
---

### Post by quaver on 2012-10-15
i am currently connected to the internet through my school proxy (its the connection am using to post this message) yet, the installer cannot detect any connection to download installation upgrades. what could be the problem and how could i solve this problem?
am currently using a12.04 live cd  on toshiba amd 64 satellite

---

### Post by darkod on 2012-10-15
Out of what ever reason, it might not be getting the proxy information correctly. Why don't you simply install without any internet connection and the internet should work later so you can do all updates?

The internel connection during install is more of a recommendation, not a requirement. The cd has everything you need.

---

### Post by cortman on 2012-10-15
+1 to Darkod's suggestion. When you want to connect to your school's proxy later then, you just need to add a line to /etc/apt/apt.conf- see [here]("https://help.ubuntu.com/community/AptGet/Howto#APT_configuration_file_method").

---

### Post by TheFu on 2012-10-15
I agree with both prior posts, but would add that you don't want any network connection at all during the install.  I did a few installs with a network connection, but no internet and it took over an hour due to all the timeouts necessary.  Without any network connection, it was 15 minutes to install.

---

### Post by quaver on 2012-10-15
i have installed successfully. the browser is working and i have tried adding a line to /etc/apt/apt.conf- and the operation was successful. when i try to update with the update manager, these are the details of what i get;
 W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://ke.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources](http://ke.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources](http://ke.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources](http://ke.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.7 80]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.7 80]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages](http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.7 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources](http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources](http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources](http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources](http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/main/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources](http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources](http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources](http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources](http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-amd64/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-amd64/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-amd64/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-amd64/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/main/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages](http://ke.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-amd64/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/main/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/universe/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/binary-i386/Packages)  407  Proxy Authentication Required [IP: 10.2.21.14 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by TheFu on 2012-10-15
Did you tell APT to use a proxy inside /etc/atp/apt.conf?

Acquire {
	Retries "0";
	HTTP {
		Proxy "http://proxy.whatever.com:8080"; 
	};
};

If authentication is required, then use the $(PROXY_USER) $(PROXY_PASS) as explained in the manpage.

**man apt.conf** should explain everything. Manpages usually explain all.

---

### Post by quaver on 2012-10-24
thank you. am good now.

---

