---
title: "Ubuntu 17.10 Unable to install Ruby"
date: 2017-10-19
forum: Installation &amp; Upgrades
---

### Post by mvoinescu on 2017-10-19
Hi there.

I have tried to set up my Ubuntu for development but when I was trying to install Ruby 2.3 using the command ```
rvm install 2.3
``` I am getting the following error
> There has been an error while updating your system using `apt-get`.It seems that there are some 404 Not Found errors for repositories listed in:


    /etc/apt/sources.list
    /etc/apt/sources.list.d/*.list


Make sure that all repositories are available from your system and verify your setup by running manually:


    sudo apt-get update


Make sure that it works correctly before proceeding with RVM.


If you are working from the GUI instead of the terminal, you might want to verify and fix broken
repositories using "Software & Updates" application.


...........
Error running 'requirements_debian_update_system ruby-2.4.1',
please read /home/mvoinescu/.rvm/log/1508410422_ruby-2.4.1/update_system.log
Requirements installation failed with status: 100.




I have also tried to follow the tutorial on [https://rvm.io/rvm/install](https://rvm.io/rvm/install) thinking that it might be due to an older version of ruby i was trying to install but resulted in the same error.

Would it be because at this point in time there is no ruby compiled for the 17.10?

Thanks

---

### Post by Kirboosy on 2017-10-19
Looking at the [RVM PPA For Ubuntu]("https://launchpad.net/~rael-gc/+archive/ubuntu/rvm") it doesn't look like there is a 17.10 build yet. Might be a bit of time before the community builds a package for 17.10.

---

### Post by mvoinescu on 2017-10-19
I understand. Now I did a test in a virtual environment where I had an Ubuntu 17.04 installed and  I did an update for it to the 17.10 and on that machine it all went well. No issue what so ever. It installed RVM and also ruby. The only thing I was wonder and I do not have the possibility to test at this moment is with a fresh install of a 17.10 in a VM. There might be a corrupted file on my machine when I did install it or something else entirely.

Looking at your response and the link it makes me think that by upgrading from 17.04 to 17.10 to have left something in the system and that way to actually install the ruby without any issues. I think I will need to downgrade the system for the time being

---

