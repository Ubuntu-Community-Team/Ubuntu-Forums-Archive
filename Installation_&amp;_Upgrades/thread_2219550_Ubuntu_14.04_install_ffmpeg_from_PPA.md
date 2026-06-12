---
title: "Ubuntu 14.04 install ffmpeg from PPA"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2014-04-24
Hi,

I need to use ffmpeg with Ubuntu 14.04. I found on the web that this PPA [https://launchpad.net/~jon-severinsson/+archive/ffmpeg](https://launchpad.net/~jon-severinsson/+archive/ffmpeg) is the "official" one to install ffmpeg  [http://www.ffmpeg.org/download.html](http://www.ffmpeg.org/download.html).
I added the PPA to the source.list with the command
```

sudo add-apt-repository 'deb http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu '"$(cat /etc/*-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f2)"' main' && sudo apt-get update

```
and then I tried to install ffmpeg but without success
```

sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ffmpeg : Depends: libavcodec54 (>= 7:1.2.5~) but 6:9.11-2ubuntu2 is to be 
installed or
                   libavcodec-extra-54 (>= 7:1.2.5~) but it is not going to be 
installed
          Depends: libavdevice53 (>= 7:1.2.5~) but it is not going to be 
installed
          Depends: libavfilter3 (>= 7:1.2.5~) but it is not going to be 
installed
          Depends: libavformat54 (>= 7:1.2.5~) but 6:9.11-2ubuntu2 is to be 
installed
E: Unable to correct problems, you have held broken packages.

```

What is the problem?
Thank you

---

### Post by Double.J on 2014-04-24
Hi there!

Just looking at the launchpad page, it advises (though in slightly confusing phrasing) to also add the saucy repo to resolve. Does this help?

I searched around a bit for you and most online guides are using [this]("https://launchpad.net/~samrog131/+archive/ppa") UNOFFICIAL ppa. Obviously do some checking and bare in mind That it does appear to be quite a large ppa that contains several different packages - so may affect other existing packages on your machine? Never add a ppa you aren't sure about!

Jj

---

### Post by erotavlas on 2014-04-25
Hi,

thank you for the reply. By adding also the repository of saucy does not help and I receive the same error. I don't want to use an unofficial repository. So what can I do?

Thank you

---

### Post by FakeOutdoorsman on 2014-04-25
14.04 no longer offers the counterfeit, so-called "ffmpeg". You can simply download a [Linux build of ffmpeg](http://ffmpeg.org/download.html#LinuxBuilds) (just download, extract, and execute; no installing needed) or follow a [step-by-step guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/UbuntuCompilationGuide).

---

### Post by erotavlas on 2014-04-30
Ok, my original problem is that I need to install openCV and as you know it requires ffmpeg. I would like to find out the easiest and safest way to install openCV. I prepared a script one for each different distribution, included debian, and so I need to modify it accordingly. The script is this:
```

version="$(wget -q -O - http://sourceforge.net/projects/opencvlibrary/files/opencv-unix | egrep -m1 -o '\"[0-9](\.[0-9])+' | cut -c2-)" 
downloadfilelist="opencv-$version.tar.gz opencv-$version.zip" 
downloadfile= 
for file in $downloadfilelist; 
do 
        wget --spider http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/$version/$file/download 
        if [ $? -eq 0 ]; then 
                downloadfile=$file 
        fi 
done 
if [ -z "$downloadfile" ]; then 
        echo "Could not find download file on sourceforge page. Please find the download file for version $version at" 
        echo "http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/$version/ and update this script" 
        exit 1 
fi 
echo "Installing OpenCV ${version}, ffmpeg and zlib" 
mkdir OpenCV 
cd OpenCV 
echo "Removing any pre-installed ffmpeg and x264" 
sudo apt-get remove ffmpeg x264 libx264-dev 
echo "Installing Dependenices ffmpeg, codecs and zlib" 
 
if [ $(cat /etc/*-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f2) == 'trusty' ]; then 
sudo add-apt-repository 'deb http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu trusty main' && sudo add-apt-repository 'deb http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu saucy main' && sudo apt-get update 
fi 
 
sudo apt-get install libopencv-dev build-essential checkinstall cmake pkg-config yasm libtiff4-dev libjpeg-dev libjasper-dev libavcodec-dev libavformat-dev libswscale-dev libdc1394-22-dev libxine-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libv4l-dev python-dev python-numpy libtbb-dev libqt4-dev libgtk2.0-dev libfaac-dev libmp3lame-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev libvorbis-dev libxvidcore-dev x264 v4l-utils ffmpeg unzip zlib1g-dev 
echo "Downloading OpenCV" $version 
wget -O $downloadfile http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/$version/$downloadfile/download 
echo "Installing OpenCV" $version 
echo $downloadfile | grep ".zip" 
if [ $? -eq 0 ]; then 
        unzip $downloadfile 
else 
        tar -xvf $downloadfile 
fi 
cd opencv-$version 
mkdir build 
cd build 
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D BUILD_SHARED_LIBS=ON -D WITH_TBB=ON -D WITH_OPENMP=ON -D WITH_OPENCL=ON -D WITH_CUDA=ON -D WITH_GTK=ON -D BUILD_NEW_PYTHON_SUPPORT=ON -D WITH_V4L=ON -D INSTALL_C_EXAMPLES=OFF -D INSTALL_PYTHON_EXAMPLES=OFF -D BUILD_EXAMPLES=OFF -D WITH_QT=ON -D WITH_OPENGL=ON -D BUILD_JPEG=ON -D BUILD_PNG=ON -D BUILD_JASPER=ON -D BUILD_ZLIB=ON -D WITH_JPEG=ON -D WITH_PNG=ON -D WITH_JASPER=ON -D WITH_ZLIB=ON -D WITH_OPENEXR=OFF .. 
make -j 2 
sudo make install 
sudo sh -c 'echo "/usr/local/lib" > /etc/ld.so.conf.d/opencv.conf' 
sudo ldconfig 
echo "OpenCV" $version "ready to be used" 

```
based on official script of ubuntu took here [https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV).
Starting from current version of Ubuntu I added the following part:
```

if [ $(cat /etc/*-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f2) == 'trusty' ]; then 
sudo add-apt-repository 'deb  http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu trusty main'  && sudo add-apt-repository 'deb  http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu saucy main'  && sudo apt-get update 
fi

```
If it works, I will be very happy.

---

### Post by erotavlas on 2014-05-01
I don't know why, but today the script has started to work well. Probably the maintainer of the PPA has changed some thing on his links.
Thank you

---

### Post by cdoublejj on 2014-06-11
i need it for tribler. it's some new greatest and latest software yet the insis of relying on ffmpeg all the while distros insist on ditching it.

---

### Post by FakeOutdoorsman on 2014-06-11
By "all the distros" I believe you mean Debian and therefore Ubuntu and kin.

---

### Post by u2nTu on 2014-08-18
**The easy way:**
```
sudo add-apt-repository ppa:jon-severinsson/ffmpeg
sudo apt-get update
sudo apt-get install ffmpeg
sudo apt-get install frei0r-plugins
```
**Takes care of all the housekeeping for you, [B]including updates.**[/B]

---

### Post by erotavlas on 2014-08-19
Yes of course the easiest way is this
```

if [ $(cat /etc/*-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f2) == 'trusty' ]; 
then  sudo add-apt-repository 'deb  http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu trusty main'  && sudo add-apt-repository 'deb  http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu saucy main'  && sudo apt-get update  
fi

```
as I specified in a previous post.

---

