This is my very first version for this tool. It has been made better with the awesome help of awesome friends, but I leave this old version here in the interest of HISTORY or just for the brave and the curious. The original README follows:

# Tools for tracking personal energy
### aka: some scripts I managed to put together with the help of friends and the internet

## WHAT IS THIS MADNESS
These are some scripts that will help me keep track of my energy level, hourly, as the day goes. It's supposed to be an interesting tool if you have ADHD or if you're autistic, and have issues dealing with energy fluctuations during the day; or if you're just curious about your **best hour** or something to that effect. Also, it spits out a nice looking chart; because numbers are confusing to look at. And I like charts a lot.

## DEPENDENCIES
[graph-cli](https://github.com/mcastorina/graph-cli) for the chart generation.

You can install it with pip: `pip install graph-cli`.

## HOW IT WORKS
### setting things up
There are 3 scripts that will do the work; first, though, you need to create a `energy.csv` file like this:

```
07:00
08:00
09:00
10:00
11:00
12:00
13:00
14:00
15:00
16:00
17:00
18:00
19:00
20:00
21:00
```

These are the hours I want to track. I suppose if you wake up at 04:00 or goes to bed at 02:00 it makes sense to adapt it to your needs. I usually wake up at 6 and go to bed at 22, so I start traking at 7 and end at 21. You do you.

Open the scripts now and edit the filepaths on the first lines of each script. 

- `energy.csv` is the file you just created;
- `av-energy.csv` will be created by one of the scripts, so it doesn't need to exist (and it gets overwritten every time); you do need to make sure the folder where you want it to be does exist;
- `energy-graph.png` will be the generated chart image (it also gets overwritten every time).

### doing the tracking
Now let's add some numbers!

I use a scale from 1 to 5: 1 is near-zero energy; 2 is low; 3 is ok; 4 is good energy; 5 is **awesome**. You can use your own scale, as long as it's made of integers. I think.

The script `te` is the main one. You just run it with the corresponding number for your current energy level as the argument. So you're having a great day: you do `te 5`. 

Done. 

It will add a `5` to the line that corresponds to the current hour. The idea is to enter one number per hour. It doesn't matter if you do it at 15:00 or 15:06 or 15:59; it'll add the number to the "15:00" row.

You're supposed to do that every hour. **Set an alarm or something.**

But what if you miss an hour? Oh no!

You could of course just open energy.csv on your favorite editor and add the proper number. But that's probably a lot of work and you wouldn't be using a script if you didn't mind opening a file and editing. 

So you can use `tt` for entering values for specific hours. Say you forgot to update your tracking at 14:00 and now it's 15:02. You do `tt 4 14` [4 because you were feeling pretty energetic and that's probably why you forgot to track your energy in the first place, and 14 because that's the hour that has passed].

**Yay.**

### doing the math
(You don't need to do any math at all. Script should take care of it.)

The third script is the fancy one that will spit the hourly average on another .csv file. This new file will be called `av-energy.csv` and will have `HORA,ENERGIA` as header. That's Portuguese for `HOUR,ENERGY`. You can change that to your own language, I suppose.

[graph-cli](https://github.com/mcastorina/graph-cli) is used for the generation of a chart in .png format. If you don't need/want the chart you can just comment out the last line of the `aven` script. You can also fiddle with options there to change color, font size and whatnot. I happen to like orange.

My own chart looks like this:

![](https://codeberg.org/olivia/energy-tracking/media/branch/main/examples/energy-graph.png)

Or maybe you have a better chart-making tool. Do tell me about it.

## WHY
I wanted a way to track my personal energy levels hourly to figure out how it fluctuated throughout the day. I wanted to be able to calculate the hourly average so I could have a simple little chart to look at.

There are several android apps that allow you to track your mood but most of them are made so you can track daily fluctuations, not hourly, so for this particular use they missed the point and didn't do me much good. I did find two equally named _Energy Tracker_ android apps [[this](https://play.google.com/store/apps/details?id=com.energon&hl=en_US&gl=US) and [this](https://play.google.com/store/apps/details?id=com.approvequestions.energytracker)] which do exactly what I want but do not export the data the way I wanted to (or at all), and having it restricted to the app wasn't something that suited me.

## IDEAS
I suppose I could make `te` and `tt` into just one script. I don't know how yet. I might try and figure it out.

## BEWARE
This is **not** a proper app. These are **not** proper scripts. I'm just a nerdy artist, definitely not a programmer. I barely know basic bash. But I'm learning and this was fun to do, I'm happy with the results, stuff work, and thought I'd share.

If you use these as an idea for something more solid, do let me know.

## THANKS
[Archie](https://jonathanh.co.uk/) helped me with bash loops and bash maths and patience. Thank you!

## FEEDBACK

"PERFECTION." - My therapist, 2021.
