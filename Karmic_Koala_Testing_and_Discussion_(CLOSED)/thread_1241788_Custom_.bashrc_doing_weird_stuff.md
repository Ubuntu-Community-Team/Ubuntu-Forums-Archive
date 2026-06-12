---
title: "Custom .bashrc doing weird stuff"
date: 2009-08-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-08-16
I put my custom .bashrc file I use in Jaunty into Karmic, and get some weird, erm, stuff. See for yourself:

---

### Post by wayne_cat on 2009-08-16
syntax error in the code :)

---

### Post by phenest on 2009-08-16
> **wayne_cat said:**
> syntax error in the code :)

It works in Jaunty.

---

### Post by wayne_cat on 2009-08-16
add this option at the beginning of the bashrc file

```
set -x
```and source the file again

```
. ./.bashrc
```you will get a verbose trace of the functions.

Can you attach the bashrc file?

---

### Post by phenest on 2009-08-16
I'll try that. It seems to work in a Karmic VM, but not in my main install.

---

### Post by slakkie on 2009-08-16
Could you post your bashrc?

---

### Post by phenest on 2009-08-16
> **slakkie said:**
> Could you post your bashrc?

I would, but I rather think there's something wrong with Karmic rather than .bashrc as it works in Jaunty and not in Karmic, which makes me think something is up with my Karmic install. And it won't be the first time.

---

### Post by slakkie on 2009-08-16
Could you? Maybe we can see where the problems lies and file a bug against bash..

---

### Post by Staz on 2009-08-16
> **phenest said:**
> I would, but I rather think there's something wrong with Karmic rather than .bashrc as it works in Jaunty and not in Karmic, which makes me think something is up with my Karmic install. And it won't be the first time.
It maybe an error in Karmic but attaching your bashrc would allow people to track down the error and eventually correct it

---

### Post by phenest on 2009-08-16
This works fine in Jaunty and in a Karmic VM, but not in a regular Karmic install.
.bashrc:
```
TRASH=$HOME/.Trash
# 0- Normal 1- Bold 2- Dark 3- ? 4- Underscore 5- ? 6- ? 7- Inverse
# 8- Invisible? 9- Strike-through
# Define a few Color's
# 0- Gray 1- Red 2- Green 3- Yellow 4- Blue 5- Magenta 6- Cyan 7- White
WHITE='e\[0;37m'
BOLDWHITE='\e[1;37m'
BOLDRED='\e[1;31m'
BOLDBLUE='\e[1;34m'
BOLDGREEN='\e[1;32m'
BOLDCYAN='\e[1;36m'
BOLDYELLOW='\e[1;33m'
NC='\e[0m'

IFS=$'\n'

PS1="\[\033[01;32m\]\u \A: \w \$\[\033[00m\] "
[ `id -u` -eq 0 ] && PS1="\[\033[01;31m\]\u: \w \$\[\033[00m\] "
PS2="\[\033[01;33m\]\u: ?\[\033[00m\] "

# aliases kept in separate file
[ -f .bash_aliases ] && . .bash_aliases

trash() {
	case $1 in
		dir)	dir -A $TRASH;;
		cd)	cd $TRASH;;
		empty)	error "Empty contents of Trash? [y/N] "; read a; [ "$a" == "y" ] && \rm -rv $TRASH/*;;
		*)	usage "trash option\noption\tdir\t- show all trash\n\tcd\t- change to trash directory\n\tempty\t- empty trash (with warning)";;
	esac
}

ppakey() { [ $# -gt 0 ] && sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com $1;}
calc() { message $1 = `echo $1 | bc`;}
fn() { unaccent UTF-8 | tr [:upper:] [:lower:] | sed 's/&/and/g' | tr / - | tr -dc [:alnum:]'- ._' | tr -s ' ' _;}
#position cursor at y,x ($1,$2)
pos() { POS='\e['$1';'$2'H'; echo -en ${POS};}
usage() { echoe $BOLDYELLOW"Usage: "$1;}
error() { echoe $BOLDRED"Error: "$1;}
message() { echoe $BOLDWHITE$1$NC; }
say() { espeak -v en/en -s 150 -g 0 -k20 -p 0 -l 100 "$1" --stdout | play -V1 -q -t wav -;}
thesaurus() { lynx -dump -nonumbers -width=240 "http://thesaurus.reference.com/browse/$1" | grep -i -e "Synonyms:\|Antonyms:" | tr -s ' ';}
define() {
	n=""
	if [ -z $2 ]; then
		n="-m 3"
	else
		[ $2 -gt 0 ] && n="-m $2"
	fi
	lynx -dump -width=640 "http://www.google.com/search?hl=en&q=define%3A+${1}&btnG=Google+Search" | grep $n "*" | tr -s ' '
}

xrotate() {
	# query xrandr to find current rotation
	if [ -n "$(xrandr | grep 'inverted (')" ]; then
		xrandr -o normal
        	#xsetwacom set "stylus" Rotate NONE
	else
		xrandr -o inverted
	        #xsetwacom set "stylus" Rotate CCW
	fi 
}

dvd2mp4() {
	[ $# -eq 0 ] && usage "dvd2mp4 options\nOptions: (n=integer $=string []=defaults)\n-play n\t\t- Play DVD title\n-file $\t\t- Video filename (no ext)\n-par n:n\t- Pixel Aspect Ratio [16:15]\n-croptop n\t- Crop top [0]\n-cropbottom n\t- Crop bottom [0]\n-cropleft\t- Crop left [0]\n-cropright\t- Crop right [0]\n-deinterlace\t- Deinterlace video\n-quality n\t- Video quantizer [26]\n-ntsc\t\t- Sets fps to 30 (29.97) and lines to 480\n-stream n\t- MPG audio stream [1]\n-title $\t- Alternative title\n-vn\t\t- Don't encode video\n-an\t\t- Don't encode audio\n-tn\t\t- Don't add tags\n-start n\t- Start position in minutes (Video only)\n-length n\t- Only encode n minutes" && return
	ct=0; cb=0; cl=0; cr=0; mpg=""; sar="16:15"; as=1; di=""; vt=""
	vn=0; an=0; tn=0; dvd=0; length=""; lt=""; start=0; vq=26
	fps=25; lines=576
	while [ $# -gt 0 ]; do
		case $1 in
			-file)		mpg=`echo $2 | sed 's/\..*//'`; vt="`echo $mpg | tr _ ' ' | caps`"; shift;;
			-par)		sar=$2; shift;;
			-croptop)	ct=$2; shift;;
			-cropbottom)	cb=$2; shift;;
			-cropleft)	cl=$2; shift;;
			-cropright)	cr=$2; shift;;
			-stream)	as=$2; shift;;
			-deinterlace)	di="-deinterlace";;
			-title)		vt=$2; shift;;
			-vn)		vn=1;;
			-an)		an=1;;
			-tn)		tn=1;;
			-play)		dvd=$2; shift;;
			-length)	lt="-t"; length=$(($2*60)); shift;;
			-start)		start=$(($2*60)); shift;;
			-quality)	vq=$2; shift;;
			-ntsc)		fps=29.97; lines=480;;
			*)		error "Unknown option: "$1; return;;
		esac
		shift
	done
	[ $dvd -gt 0 ] && [ -z $mpg ] && mplayer dvd://$dvd -aid 128 && return
	[ -z $mpg ] && error "You must specify a filename" && return
	[ $dvd -gt 0 ] && mplayer dvd://$dvd -dumpstream -dumpfile $mpg.mpg
	[ ! -f $mpg.mpg ] && error "File "$mpg.mpg" doesn't exist!" && return
	[ $vn -eq 0 ] && w=$((720-$cl-$cr)) && h=$(($lines-$ct-$cb)) && ffmpeg -i $mpg.mpg -an $di $lt $length -ss $start -s 720x$lines -croptop $ct -cropbottom $cb -cropleft $cl -cropright $cr -f rawvideo - | x264 -q $vq --sar $sar -o video.mp4 - ${w}x$h --fps $fps
	[ $an -eq 0 ] && ffmpeg -y $lt $length -i video.mp4 -vcodec copy -i $mpg.mpg -acodec libfaac -aq 200 -ac 2 -ar 22050 -async 1 -r $fps -map 0:0 -map 1:$as $mpg.mp4
	[ $tn -eq 1 ] && return
	tf=`echo $mpg | sed 's/_.*//'`
	if [ -e $tf ]; then
		series=`echo $mpg | sed 's/.*-//' | sed 's/_.*//'`
		episode=`echo $mpg | sed 's/.*_//'`
		tags=(`cat $tf`)
		artist=${tags[0]}
		title=${tags[$episode]}
		fn=`echo "$artist-$series $episode" | fn`.mp4
		message "$artist - Series $series\nEpisode $episode - $title\n$fn"$NC
		mv $mpg.mp4 $fn
		mp4tags -A "$artist - Series "$series -s "$title" $fn
	else
		message "Adding title: "$vt
		mp4tags -s "$vt" $mpg.mp4
	fi
}

cd2m4a() {
	[ $# -eq 0 ] && usage "cd2m4a options\nOptions: (n=integer $=string)\n-play n\t\t- Play track from CD\n-artist $\t- Artist\n-album $\t- Album\n-year n\t\t- Year\n-genre $\t- Genre\n-title $\t- Alternative title (for use with -single)\n-tn\t\t- Don't use 'taginfo' file\n-multi\t\t- Multiple artists\n-single n\t- Rip one track only e.g. 4 or 2-5\nThe tag info file should be called 'taginfo' and list the track names. For multiple artists, the artist and year should be included before each track name." && return
	artist=""; album=""; year=0; ma=0; st=0; title=""; tn=0
	while [ $# -gt 0 ]; do
		case $1 in
			-play)		message "Playing track "$2" from CD (ctrl-c to end)"; gst-launch playbin uri=cdda://$2; return;;
			-artist)	artist="$2"; shift;;
			-album)		album="$2"; shift;;
			-year)		year=$2; shift;;
			-genre)		genre="$2"; shift;;
			-tn)		tn=1;;
			-multi)		ma=1;;
			-single)	st=$2; shift;;
			-title)		title="$2"; shift;;
			*)		error "Unknown option: "$1; return;;
		esac
		shift
	done
	[ $ma -eq 0 ] && message "Artist\t$artist"
	[ ! -z $album ] && message "Album\t$album"
	[ $ma -eq 0 ] && [ $year -gt 0 ] && message "Year\t$year"
	[ ! -z $genre ] && message "Genre\t$genre"
	tags=(`cat "taginfo"`)
	tr=1; tp=0
	[ $st -gt 0 ] && tr=$st
	until [ $tp -eq ${#tags[@]} ]; do
		if [ $ma -eq 1]; then
			artist=${tags[$tp]}
			year=${tags[$(($tp+1))]}
			message "Artist:\t$artist\nYear:\t$year"
			let tp+=2
		fi
		title=${tags[$tp]}
		let tp+=1
		message "$tr\t$title"
		file=(`echo "$tr.$title" | fn`)
		cdparanoia $tr cdda.wav
		ffmpeg -y -i cdda.wav -acodec libfaac -aq 200 $file.m4a && mp4tags -a "$artist" -s "$title" -A "$album" -t $tr $file.m4a
		[ ! -z $year ] && mp4tags -y $year $file.m4a
		[ ! -z $genre ] && mp4tags -g $genre $file.m4a
		[ $st -gt 0 ] && break
		#mp4tags -r cw
		let tr+=1
	done
	/rm cdda.wav
}


#change desktop background
change_background() {
	[ $# -lt 2 ] && usage "change_background path style\npath\t- Path to folder containing background pictures\nstyle\t- none centered wallpaper scaled stretched zoom" && return
	files=(`find $HOME/$1 | grep -i "\.jpg$\|\.gif$\|\.png$\|\.bmp$"`)
	# Set a random wallpaper with gconftool-2
	gconftool-2 -t str --set /desktop/gnome/background/picture_filename "`echo ${files[RANDOM%${#files[@]}]}`"
	gconftool-2 -t str --set /desktop/gnome/background/picture_options $2
}

# Random PSK generator
rpwg() {
	[ $# -eq 0 ] && usage "rpwg type [length] \ntype\t-p psk\n\t-a alphanumeric\nlength\tbetween 8 and 63 (omit for random)" && return
	# Characters - no space as it could be confusing if leading or trailing
	characters=('0' '1' '2' '3' '4' '5' '6' '7' '8' '9' 'A' 'B' 'C' 'D' 'E' 'F' 'G' 'H' 'I' 'J' 'K' 'L' 'M' 'N' 'O' 'P' 'Q' 'R' 'S' 'T' 'U' 'V' 'W' 'X' 'Y' 'Z' 'a' 'b' 'c' 'd' 'e' 'f' 'g' 'h' 'i' 'j' 'k' 'l' 'm' 'n' 'o' 'p' 'q' 'r' 's' 't' 'u' 'v' 'w' 'x' 'y' 'z' '[' '\' ']' '^' '_' "'" ':' ';' '<' '=' '>' '?' '@' '!' '"' '#' '$' '%' '&' '`' '(' ')' "*" '+' ',' '-' '.' '/' '{' '|' '}' '~')
	let l=RANDOM%56+8
	[ ! -z $2 ] && l=$2
	[ $l -lt 8 ] && error "Less than 8 characters won't give very good security" && return
	[ $l -gt 63 ] && error "Maximum of 63 characters allowed" && return
	case $1 in
		-p)	n=${#characters[@]};;
		-a)	n=62;;
		*)	error "Invalid type"; return;;
	esac
	s=""
	while [ $l -gt 0 ]; do
		let r=RANDOM%n
		s=$s${characters[$r]}
		let l-=1
	done
	message $s
}

# Easy extract
extract () {
	[ ! -f $1 ] && error "'$1' is not a valid file!" && return
	case $1 in
		*.tar.bz2)	tar xvjf $1;;
		*.tar.gz)	tar xvzf $1;;
		*.bz2)		bunzip2 $1;;
		*.rar)		rar x $1;;
		*.gz)		gunzip $1;;
		*.tar)		tar xvf $1;;
		*.tbz2)		tar xvjf $1;;
		*.tgz)		tar xvzf $1;;
		*.zip)		unzip $1;;
		*.Z)		uncompress $1;;
#		*.7z)		7z x $1;;
		*)		message "Don't know how to extract '$1'...";;
	esac
}

#welcome message
pos 2 30
echo -e $BOLDRED`uname -smr`
pos 6 30
echo -e $BOLDBLUE"Hello $USER" | caps
pos 1 1
echo -en $BOLDWHITE
cal -m
#echo -e $NC
#say "Hello $USER"
```
.bash_aliases:
```
alias bash='clear; \bash'
alias edit_bashrc='gedit ~/.bashrc &'
alias rm='mv -b -t $TRASH/'
alias dir='\dir --color=auto'
alias help="alias | sed 's/=.*//'; set | grep '() $' | grep -v 'command_not_found_handle.*'"
alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias install='sudo apt-get install'
alias remove='sudo apt-get remove'
alias today='grep -h -d skip `date +%m/%d` /usr/share/calendar/*'
alias xgrab='ffmpeg -f x11grab -s wuxga -r 60 -i :0.0 -qscale 1 -r 25 -s 960x600 grab.mp4'
alias caps="sed 's/[^ ]*/\u&/g'"
alias x264='x264 -m 9 --me tesa --merange 24 -r 3 --mixed-refs --no-fast-pskip -t 2 -f 0:0 -A all -b 15 -8 --b-pyramid -w --direct auto --threads 0 --progress'
alias nano='nano -xwmicS'
alias echoe='echo -e'
```
I've gone through and installed all packages needed for each alias and function to work. I may have missed something but I am a little tired.

EDIT: To see the problem as shown in my screenshot, type in something in the terminal that you know bash won't understand.

---

### Post by slakkie on 2009-08-16
It is related to the IFS you set, when you remove it the error disappears. Why you set this globally I don't know, but it is not a good plan IYAM. If you need it for a particular application/function, store the old IFS value and reset it back once you're done:

```

OLD_IFS=$IFS
IFS=newvalue
# more code
IFS=$OLD_IFS

```

And for you extract function:

```

extract () {
        for i in $@
        do
                [ ! -f "$i" ] || [ ! -r "$i" ] && echo "'$i' is not present or could not be read" && continue
                case $i in
                        (*.tar.bz2|*.tbz2) bzip2 -dc $i | tar xvf - ;;
                        (*.tar.gz|*.tgz) gzip -dc $i | tar xvf - ;;
                        (*.bz2) bzip2 -dc $i ;;
                        (*.rar) rar x $i ;;
                        (*.gz) gzip -d $i ;;
                        (*.tar) tar xvf $i ;;
                        (*.zip) unzip $i ;;
                        (*.Z) uncompress $i ;;
                        (*.7z) 7z x $i ;;
                        (*.deb) ar xv $i ;;
                        (*) echo "'$i' cannot be extracted via extract()" ;;
                esac
        done
}

```

---

### Post by phenest on 2009-08-17
> **slakkie said:**
> It is related to the IFS you set, when you remove it the error disappears.

Any idea why the problem doesn't exist in Jaunty?

---

### Post by slakkie on 2009-08-17
> **phenest said:**
> Any idea why the problem doesn't exist in Jaunty?

No, I had a quick peek, saw your IFS, commented and the error disappeared. I need to remove whole parts of your bashrc to see what triggers the error. But I do know that the IFS is definitely a source of your problem.

---

### Post by VMC on 2009-08-17
Thanks for bringing this topic up.I need to do the same thing - copy jaunty bashrc to karmic and see the results.

There's some good comments here to consider.

---

### Post by wayne_cat on 2009-08-17
> **phenest said:**
> Any idea why the problem doesn't exist in Jaunty?

phenest,

I had a little bit time to trace the functions from the file. Could you please try this:

** 1. Copy your bashrc to a folder (i.e. /tmp)**

```
cp ~/.bashrc /tmp/test_bashrc
```---------------------------------------------------
** 2. remove the caps package (if installed)**

```
sudo apt-get remove caps
```---------------------------------------------------
** 3. Create a dummy file **

```
sudo touch /usr/bin/caps && chmod +x /usr/bin/caps
```---------------------------------------------------
** 4. open a terminal and source the file in /tmp**

```
source /tmp/test_bashrc
```-------------------------------------------------------

Now you should see this in the terminal (no error message)

```
    August 2009     esktop$ cp bashh /tmp/test_bashrc
Mo Di Mi Do Fr Sa Soesktop$ sLinux 2.6.31-6-generic i686
                1  2
 3  4  5  6  7  8  9
10 11 12 13 14 15 16
17 18 19 20 21 22 23
24 25 26 27 28 29 30
31                  
rschmitt 18:40: ~/Desktop $ 


```What is your result?

---

### Post by slakkie on 2009-08-17
I need to go home, but I've managed to get a bit closer to the problem:

You will hit this bug if you set the IFS like you did and you type a command which is NOT in your path. If I unset the IFS, and then type a command which is not in my path, it just resumes as normal.

For me the problem started at the say() function, which uses the play command (which I don't have installed):

```

wesleys 19:04: ~ $ play
bash: read: 10573 (bash) R 10565 10573 10532 34821 10573 4194368 150 0 0 0 0 0 0 0 20 0 1 0 2782406 5160960 320 4294967295 134512640 135280036 3220955744 3220953764 9405474 0 0 0 1266695929 0 0 0 17 1 0 0 0 0 0: syntax error in expression (error token is "(bash) R 10565 10573 10532 34821 10573 4194368 150 0 0 0 0 0 0 0 20 0 1 0 2782406 5160960 320 4294967295 134512640 135280036 3220955744 3220953764 9405474 0 0 0 1266695929 0 0 0 17 1 0 0 0 0 0")
wesleys 19:04: ~ $ ls -altr | head -1
total 1122024
wesleys 19:04: ~ $ unset IFS
wesleys 19:05: ~ $ play
The program 'play' is currently not installed.  You can install it by typing:
sudo apt-get install sox
bash: play: command not found
wesleys 19:05: ~ $

```

If you append set -x at the end of your bashrc, you will see this information, when a command (not found) is entered:

```

lt
+ lt
+ local cmd state rest
+ local -i pid ppid pgrp session tty_nr tpgid
+ test -n '' -o '!' -t 1
+ read pid cmd state ppid pgrp session tty_nr tpgid rest
bash: read: 10599 (bash) R 10593 10599 10532 34821 10599 4194368 168 0 0 0 0 0 0 0 20 0 1 0 2804794 5160960 333 4294967295 134512640 135280036 3219860320 3219858340 7083042 0 0 0 1266695929 0 0 0 17 1 0 0 0 0 0: syntax error in expression (error token is "(bash) R 10593 10599 10532 34821 10599 4194368 168 0 0 0 0 0 0 0 20 0 1 0 2804794 5160960 333 4294967295 134512640 135280036 3219860320 3219858340 7083042 0 0 0 1266695929 0 0 0 17 1 0 0 0 0 0")

```

Behaviour when typing in a command when IFS is set correctly:

```

wesleys 19:10: ~ $ ll
+ ll
+ local cmd state rest
+ local -i pid ppid pgrp session tty_nr tpgid
+ test -n '' -o '!' -t 1
+ read pid cmd state ppid pgrp session tty_nr tpgid rest
+ test 10640 -eq 10645
+ '[' -x /usr/lib/command-not-found ']'
+ /usr/bin/python /usr/lib/command-not-found -- ll
+ return 127
bash: ll: command not found

```

Why this is, I cannot tell you, since I'm not really into the internals of bash, but your combi has to do with your IFS and command lookups, which fails...

You need to have a space set in your IFS for this bug NOT to happen.

---

### Post by phenest on 2009-08-17
> **slakkie said:**
> No, I had a quick peek, saw your IFS, commented and the error disappeared.

I understand that the IFS is the cause of the problem, but wondered why it's ok in Jaunty, i.e. is there a difference in Bash in Karmic. If I login to a tty, I get access to this script in Karmic, but not in Jaunty. I appreciate there may be something wrong with my script, but I'd hate to blame the script to find there are bugs in Bash.

> **wayne_cat said:**
> phenest,

I had a little bit time to trace the functions from the file. Could you please try this:

** 1. Copy your bashrc to a folder (i.e. /tmp)**

```
cp ~/.bashrc /tmp/test_bashrc
```---------------------------------------------------
** 2. remove the caps package (if installed)**

```
sudo apt-get remove caps
```---------------------------------------------------
** 3. Create a dummy file **

```
sudo touch /usr/bin/caps && chmod +x /usr/bin/caps
```---------------------------------------------------
** 4. open a terminal and source the file in /tmp**

[code]

Why have you targeted the caps package? You do realise that caps is an alias that calls sed?

---

### Post by wayne_cat on 2009-08-17
> **phenest said:**
> I understand that the IFS is the cause of the problem, but wondered why it's ok in Jaunty, i.e. is there a difference in Bash in Karmic. If I login to a tty, I get access to this script in Karmic, but not in Jaunty. I appreciate there may be something wrong with my script, but I'd hate to blame the script to find there are bugs in Bash.



Why have you targeted the caps package? You do realise that caps is an alias that calls sed?


ahh .. sorry ... did not see your 2nd listing with the aliases. OK ... I have added these
aliases , remove /usr/bin/caps and this is my result if I start a new terminal:

[[IMG]http://ubuntu-pics.de/thumb/22233/terminal_CA2e4G.png[/IMG]]("http://ubuntu-pics.de/bild/22233/terminal_CA2e4G.png")

Is this what you expected to see?

---

### Post by slakkie on 2009-08-17
I've asked a mate of mine to test it on Jaunty:

```

beeman@crimson:~$ IFS=""
beeman@crimson:~$ set -x
beeman@crimson:~$ a-command-not-found
+ a-command-not-found
+ '[' -x /usr/lib/command-not-found ']'
+ /usr/bin/python /usr/lib/command-not-found -- a-command-not-found
+ return 127
-bash: a-command-not-found: command not found

```

Same bash version as on Jaunty.

I think it might be related to the package: command-not-found

Looking into it now.

---

### Post by slakkie on 2009-08-17
Yes, if you remove the package command not found it you don't get the error.. File a bug against that package, that one has changed since Jaunty.

---

### Post by taavikko on 2009-08-17
> **slakkie said:**
> File a bug against that package, that one has changed since Jaunty.

Just a side note:

command-not-found
```
karmic	development	main	release	0.2.37ubuntu2  
jaunty	current	main	release	0.2.34ubuntu3
```

---

### Post by wayne_cat on 2009-08-17
> **slakkie said:**
> Yes, if you remove the package command not found it you don't get the error.. File a bug against that package, that one has changed since Jaunty.

confirmed ... after installing command-not-found I also get the error

---

### Post by phenest on 2009-08-17
> **wayne_cat said:**
> Is this what you expected to see?

Yep, that's what I get. Now type a command that doesn't exist, say 'blah'. Normally, the result is: bash: blah: command not found. But not in Karmic (at least for me), where I get all that garbled rubbish.

---

### Post by phenest on 2009-08-17
Ok. So it's command-not-found. Thanks taavikko.

---

### Post by wayne_cat on 2009-08-17
> **phenest said:**
> Yep, that's what I get. Now type a command that doesn't exist, say 'blah'. Normally, the result is: bash: blah: command not found. But not in Karmic (at least for me), where I get all that garbled rubbish.

I have removed command-not-found right after the installation on Alpha1 ... no wonder
that I did not get the error

---

### Post by slakkie on 2009-08-17
> **phenest said:**
> Ok. So it's command-not-found. Thanks [s]taavikko[/s]**slakkie**.

Credits due where credits due.

---

### Post by phenest on 2009-08-17
> **slakkie said:**
> Why you set this globally I don't know, but it is not a good plan IYAM.

Because it worked and it's very lazy of me. I do know better. I'm actually an accomplished programmer in many languages. I just get lazy sometimes and then forget to go back and do it properly. :D Although you could replace 'forget' in that last sentence with 'don't bother'. ;)

---

### Post by taavikko on 2009-08-17
> **slakkie said:**
> Credits due where credits due.

Yep, I had no part in this, slakkie and wayne_cat is to be praised.

---

### Post by phenest on 2009-08-17
> **slakkie said:**
> Credits due where credits due.

Sorry. Thanks everyone.

---

### Post by slakkie on 2009-08-17
Create bug report [https://bugs.launchpad.net/bugs/415030](https://bugs.launchpad.net/bugs/415030)

---

### Post by wayne_cat on 2009-08-17
> **slakkie said:**
> Create bug report [https://bugs.launchpad.net/bugs/415030](https://bugs.launchpad.net/bugs/415030)

confirmed and subscribed

---

