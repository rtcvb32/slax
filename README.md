# slax
Slax related OS stuff


Slax is a great slim OS that's modular and uses SquashFS (My favorite FS to date!).
However it can be slow, VERY slow in VM's and hardware due to using LZMA/XZ compression. While this compression is GREAT for limited sizes, this isn't so useful when you want to use it as an actual device. On a VM it's taken me minutes to boot up or longer.

So this is my solution. A (hopefully) full featured script you run within Slax that will recompress your sb files to use LZO compression instead of XZ by default.

As a bonus adds the touch-to-tap file in the Desktop bundle so expected behavior for touchpads is present. (If you don't like this, just delete the file at /etc/X11/xorg.conf.d/40-libinput.conf)

Usage:

To use the script all you have to do is download it, and run while referencing the mounted directory for where the bundles are located.

curl:

apt update; apt-get install curl

Getting and activating script:

cd /tmp; curl https://raw.githubusercontent.com/rtcvb32/slax/main/slax2lzo -o slax2lzo; chmod +x slax2lzo
./slax2lzo [ DIRECTORY LOCATION, like /media/sda1 ]
 
 If all goes well it should extract all the sb's that are important, repack them, add the lzo files and the touchpad file, and then write it back to where it got it all at and immediately restart the system. Just to be sure, run in 'Fresh Start' to make sure unneeded changes are gone.
 
 new script files should include savechanges_lzo dir2sb_lzo
 
 In the event you want to process sb files without adding anything new, sb2lzo is the script for you. Using slax scripts it will extract and then repack sb files.
