---
title: "Error reading from server. Remote end closed connection"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by phidia on 2007-04-23
I keep getting the error I pasted into the title in apt-get. I have done update and I've found that I can eventually download the package I'm trying to get but I have to babysit the computer because  apt will stop with the "some packages failed to install..." message. I'm on a slow connection.

The strange thing is I almost never had this problem with dapper or edgy.  I get this problem now in feisty with almost everything I try to install.
Is there some value I can edit in apt to keep my connection with the repo server?

Added later
This is just a lot of work because apt/the server will close on one of the dependencies and then jump to another before it eventually gives up and gives that "some packages failed to install..." Re-starting the dl eventually succeeds but it is time consuming since I have to monitor apt all the time. I may go back to edgy if there isn't a solution to this.

---

### Post by phidia on 2007-04-26
Error reading from server. Remote end closed connection [IP: 130.239.18.158 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Even using apt-get to install a relatively small package (approx 3Mb) i get the above error about a dozen times before it finally completes. Apt did eventually finish and installed the app but why is this happening now?

---

