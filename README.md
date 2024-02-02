function validateLRN(input) {
    const inputValue = input.value;
    const numericValue = inputValue.replace(/[^0-9]/g, '');
    const remainingDigits = 12 - numericValue.length;

    if (numericValue.length === 12) {
        // If exactly 12 digits, set border color to green and display "Valid" message below the input
        input.style.borderColor = 'cornflowerblue';
        document.getElementById('lrnError').innerHTML = '<span style="color: green;">&#10004; Valid</span><br>';
    } else {
        // If less or more than 12 digits, set border color to red
        input.style.borderColor = 'lightcoral';

        // Display error message based on remaining digits
        const errorSpan = document.getElementById('lrnError');
        if (/[^0-9]/.test(inputValue)) {
            errorSpan.textContent = 'LRN should only contain numbers.';
        } else if (remainingDigits > 0) {
            errorSpan.textContent = `Enter ${remainingDigits} more digit${remainingDigits > 1 ? 's' : ''} for LRN.`;
        } else {
            errorSpan.textContent = '';
        }
    }

    // Update input value with sanitized numeric value
    input.value = numericValue.slice(0, 12);
}

document.getElementById('lrn').addEventListener('input', function () {
    validateLRN(this);
});

function validatePassword(input) {
    const passwordValue = input.value;

    const errorSpan = document.getElementById('passwordError');
    if (passwordValue.length < 8) {
        errorSpan.textContent = 'Password should be at least 8 characters.';
        input.style.borderColor = 'lightcoral';
    } else {
        errorSpan.textContent = '';
        input.style.borderColor = 'cornflowerblue';
    }
}

document.getElementById('password').addEventListener('input', function () {
    validatePassword(this);
});

document.getElementById('loginButton').addEventListener('click', function () {
    // Disable the button during the animation
    this.disabled = true;

    const lrnValue = document.getElementById('lrn').value;
    const passwordValue = document.getElementById('password').value;

    // Check if LRN and Password are both valid
    if (lrnValue.length === 12 && passwordValue.length >= 8) {
        // Show loading message for 3.5 seconds
        showNotification('Logging in...', '#3498db', 3500);

        // Simulate a 3.5-second loading effect
        setTimeout(() => {
            // Redirect to another page (replace 'target-page.html' with the actual target page)
            window.location.href = 'Dashboard.html';
        }, 3500);
    } else {
        // Show login unsuccessful notification for 3.5 seconds
        showNotification('Login unsuccessful. Please check your LRN and Password.', 'red', 3500);
    }
});


// Function to show the notification with adjustable duration
function showNotification(message, color, duration) {
    const notificationContainer = document.getElementById('notificationContainer');
    const notificationText = document.getElementById('notificationText');

    // Set the notification message and color
    notificationText.innerHTML = message.replace(/\n/g, '<br>');
    notificationContainer.style.backgroundColor = color;

    // Show the notification with animation
    notificationContainer.style.opacity = '1';
    notificationContainer.style.transform = 'translateY(0)';

    // Hide the notification after the specified duration
    setTimeout(() => {
        notificationContainer.style.opacity = '0';
        notificationContainer.style.transform = 'translateY(-50px)';
        // Re-enable the button
        document.getElementById('loginButton').disabled = false;
    }, duration);
}

document.getElementById('loginButton').addEventListener('click', function () {
    const lrnValue = document.getElementById('lrn').value;
    const passwordValue = document.getElementById('password').value;

    // Check if LRN and Password are both valid
    if (lrnValue.length === 12 && passwordValue.length >= 8) {
        // Disable the button during the animation
        this.disabled = true;

        // Show the loader
        document.querySelector('.loader-container').style.display = 'flex';

        // Simulate a 3.5-second loading effect
        setTimeout(() => {
            // Redirect to another page (replace 'target-page.html' with the actual target page)
            window.location.href = 'Dashboard.html';
        }, 3500);
    } else {
        // Show login unsuccessful notification for 3.5 seconds
        showNotification('Login unsuccessful. Please check your LRN and Password.', 'red', 3500);
    }
});

// Function to show the notification with adjustable duration
function showNotification(message, color, duration) {
    const notificationContainer = document.getElementById('notificationContainer');
    const notificationText = document.getElementById('notificationText');

    // Set the notification message and color
    notificationText.innerHTML = message.replace(/\n/g, '<br>');
    notificationContainer.style.backgroundColor = color;

    // Show the notification with animation
    notificationContainer.style.opacity = '1';
    notificationContainer.style.transform = 'translateY(0)';

    // Hide the notification after the specified duration
    setTimeout(() => {
        notificationContainer.style.opacity = '0';
        notificationContainer.style.transform = 'translateY(-50px)';
        // Re-enable the button
        document.getElementById('loginButton').disabled = false;
    }, duration);
}

document.getElementById('loginButton').addEventListener('click', function () {
    const lrnValue = document.getElementById('lrn').value;
    const passwordValue = document.getElementById('password').value;

    // Check if LRN and Password are both valid
    if (lrnValue.length === 12 && passwordValue.length >= 8) {
        // Disable the button during the animation
        this.disabled = true;

        // Show the loader with fading animation
        const loaderContainer = document.getElementById('loaderContainer');
        loaderContainer.style.display = 'flex';
        loaderContainer.style.backgroundColor = 'rgba(255, 255, 255, 0.8)';
        loaderContainer.style.opacity = '1';

        // Simulate a 3.5-second loading effect
        setTimeout(() => {
            // Redirect to another page (replace 'target-page.html' with the actual target page)
            window.location.href = 'Dashboard.html';
        }, 3500);
    } else {
        // Show login unsuccessful notification for 3.5 seconds
        showNotification('Login unsuccessful. Please check your LRN and Password.', 'red', 3500);
    }
});

function showNotification(message, color, duration) {
    const notificationContainer = document.getElementById('notificationContainer');
    const notificationText = document.getElementById('notificationText');

    // Set the notification message and color
    notificationText.innerHTML = message.replace(/\n/g, '<br>');
    notificationContainer.style.backgroundColor = color;

    // Show the notification with fade-in animation
    notificationContainer.style.opacity = '0';
    notificationContainer.style.transform = 'translateY(-50px)';

    setTimeout(() => {
        notificationContainer.style.opacity = '1';
        notificationContainer.style.transform = 'translateY(0)';
        notificationContainer.style.transition = 'opacity 0.3s ease, transform 0.3s ease';
    }, 10); // A small delay to ensure the styles are applied before the transition

    // Hide the notification after the specified duration
    setTimeout(() => {
        // Hide the notification with fade-out animation
        notificationContainer.style.opacity = '0';
        notificationContainer.style.transform = 'translateY(-50px)';
        
        // Re-enable the button
        document.getElementById('loginButton').disabled = false;
    }, duration);
}

document.getElementById('loginButton').addEventListener('click', function () {
    const lrnValue = document.getElementById('lrn').value;
    const passwordValue = document.getElementById('password').value;

    // Check if LRN and Password are both valid
    if (lrnValue.length === 12 && passwordValue.length >= 8) {
        // Disable the button during the animation
        this.disabled = true;

        // Show the loader with fading animation
        const loaderContainer = document.getElementById('loaderContainer');
        loaderContainer.style.display = 'flex';
        loaderContainer.style.backgroundColor = 'rgba(255, 255, 255, 0.8)';
        loaderContainer.style.opacity = '1';

        // Simulate a 3.5-second loading effect
        setTimeout(() => {
            // Redirect to another page (replace 'target-page.html' with the actual target page)
            window.location.href = 'Dashboard.html';
        }, 3500);
    } else {
        // Show login unsuccessful notification for 3.5 seconds
        showNotification('Login unsuccessful. Please check your LRN and Password.', 'red', 3500);
    }
});

function showNotification(message, color, duration) {
    const notificationContainer = document.getElementById('notificationContainer');
    const notificationText = document.getElementById('notificationText');

    // Set the notification message and color
    notificationText.innerHTML = message.replace(/\n/g, '<br>');
    notificationContainer.style.backgroundColor = color;

    // Show the notification with fade-in animation
    notificationContainer.style.opacity = '0';
    notificationContainer.style.transform = 'translateY(-50px)';

    setTimeout(() => {
        notificationContainer.style.opacity = '1';
        notificationContainer.style.transform = 'translateY(0)';
        notificationContainer.style.transition = 'opacity 0.3s ease, transform 0.3s ease';
    }, 10); // A small delay to ensure the styles are applied before the transition

    // Hide the notification after the specified duration
    setTimeout(() => {
        // Hide the notification with fade-out animation
        notificationContainer.style.opacity = '0';
        notificationContainer.style.transform = 'translateY(-50px)';

        // Re-enable the button
        document.getElementById('loginButton').disabled = false;
    }, duration);
}

