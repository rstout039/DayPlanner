var p = MindFusion.Scheduling;

// create a new instance on the calendar //
var calendar = new p.Calendar(document.getElementById("calendar"));

calendar.theme = "peach"

// visualize the calendar //
calendar.render();

calendar.itemCreating.addEventListener(handleItemCreating);
calendar.itemModified.addEventListener(handleItemModified);
calendar.itemDeleting.addEventListener(handleItemDeleting);

function handleItemDeleting(sender, args){

        args.cancel = true
        showWarning("You are not allowed to delete an item");
}
function handleItemCreating(sender, args){
    if(itemOnSunday(args.item) || itemTooLate(args.item)){
        args.cancel = true;
        showWarning("Items can't occur on Sunday nor take place after 8pm");
    }
}
function handleItemModified(sender, args){
    if(itemOnSunday(args.item) || itemTooLate(args.item)){
        args.item.startTime = args.oldItem.startTime
        args.item.endTime = args.oldItem.endTime
        showWarning("Items can't occur on Sunday nor take place after 8pm");
    }
}
function itemOnSunday(item){
    if(item.startTime.dayOfWeek === 0 || item.endtime.dayOfWeek === 0){
        return true;
    }
    var startTime = item.startTime.clone();
    while(startTime.compareTo(item.endTime)<= 0){
        if(startTime.dayOfWeek === 0){
            return true;
        }
        startTime.addDays(1)
    }
    return false;
}
function itemTooLate(item){
    if(item.startTime.hour > 20 || item.endTime.hour > 20){
        return true;
    }
    return false;
}
function showWarning(message_text){
    document.getElementById("alrt").innerHTML = message_text;
    setTimeout(function() {document.getElementById("alrt").innerHTML = "";},5000);
}
