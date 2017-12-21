# Using ffmpeg to make plot movies

ffmpeg -framerate 24 -i tic1_%03d.png -framerate 24 -i final.tic1.%05d.tga -c:v libx264 -vcodec libx264 -pix_fmt yuv420p -preset slow -crf 18 -filter_complex "[0:v]scale=768:512 [left] ;[1:v]scale=512:512 [right]; [left][right] hstack" movie1.mp4

LOTS OF THINGS TO DISCUSS HERE!!!!

-framerate 24
You can change this to speed up or slow down your movie. The output framerate is given by the -r option.
-c:v libx264
Use H.264 to encode your movie. This is a good, well-supported encoding that seems to be everyone’s favorite.
-preset slow
Try hard to reduce the file size. It’s not that slow.
-crf 18
“Quality”. This means essentially lossless. Higher is worse. ffmpeg documentation here and explanation here.
-r 24
Output frame rate. If you are speeding up your rendered frames with -framerate > 24, make sure you set this or your movie will look jittery in Powerpoint.